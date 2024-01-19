if [ ! -f "$hosts_file" ]; then
    echo "Error: hosts file '$hosts_file' not found."
    exit 1
fi

# Read each host from the file
while IFS= read -r host; do
    echo "Copying SSH key to $host..."

    # Try each password until successful or none left
    for password in "${passwords[@]}"; do
        if sshpass -p "$password" ssh-copy-id admin@"$host"; then
            echo "SSH key deployment successful for $host."
            break  # Break the loop if successful
        else
            echo "Failed to copy SSH key using password: $password"
        fi
    done

done < "$hosts_file"

echo "SSH key deployment complete."

                                       
