📌 Overview
This lab demonstrates how two files that appear identical can actually be different at the binary level.
By generating SHA-256 hashes and comparing them, you can detect even the smallest changes in file content.

🗂 Scenario
You are working in /home/analyst with two files:

Copy
Edit
file1.txt
file2.txt
Both files look the same when viewed with cat, but hashing will reveal they are different.

🛠 Commands Used
ls – List directory contents

cat – Display file contents

sha256sum – Generate SHA-256 hash values

>> – Append output to a file

cmp – Compare files byte by byte

📖 Step-by-Step Instructions
1. Verify File Contents
bash
Copy
Edit
ls
cat file1.txt
cat file2.txt
Both display:

ruby
Copy
Edit
X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*
2. Generate SHA-256 Hashes
bash
Copy
Edit
sha256sum file1.txt
sha256sum file2.txt
Example output:

Copy
Edit
131f95c51cc819465fa1797f6ccacf9d494aaaff46fa3eac73ae63ffbdfd8267  file1.txt
2558ba9a4cad1e69804ce03aa2a029526179a91a5e38cb723320e83af9ca017b  file2.txt
🔹 Even though the text looks the same, hashes are different.

3. Save Hashes to Separate Files
bash
Copy
Edit
sha256sum file1.txt >> file1hash
sha256sum file2.txt >> file2hash
4. Compare Hash Files
bash
Copy
Edit
cat file1hash
cat file2hash
Then compare byte by byte:

bash
Copy
Edit
cmp file1hash file2hash
Output:

arduino
Copy
Edit
file1hash file2hash differ: char 1, line 1
✅ Confirms that the files differ internally.

💡 Key Takeaways
Files that look identical in plain text may differ in hidden characters, metadata, or encoding.

Hashes are a reliable way to verify file integrity.

Even a 1-bit change in a file produces a completely different hash (the avalanche effect).

cmp is useful for pinpointing exactly where differences occur.

