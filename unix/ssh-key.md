# SSH key

1. Generate key
`ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`

2. Start ssh-agent in background
`eval "$(ssh-agent -s)"`

3. Add ssh key to ssh-agent
`ssh-add ~/.ssh/id_rsa`

4. Add to git account
`xclip -sel clip < ~/.ssh/id_rsa.pub`
