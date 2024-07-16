https://decapcms.org/docs/hugo/

1. creare struttura base hugo
    * layout
    * baseof
    * head
2. Creare cartella "admin" dentro cartella sito "static"
    /static/admin
    * file config.yml
    '''
    backend:
    name: git-gateway
    branch: main # Branch to update (optional; defaults to master)
    media_folder: static/img
    public_folder: /img
    collections:
    - name: 'blog'
        label: 'Blog'
        folder: 'content/blog'
        create: true
        slug: '{{year}}-{{month}}-{{day}}-{{slug}}'
        editor:
        preview: false
        fields:
        - { label: 'Title', name: 'title', widget: 'string' }
        - { label: 'Publish Date', name: 'date', widget: 'datetime' }
        - { label: 'Description', name: 'description', widget: 'string' }
        - { label: 'Body', name: 'body', widget: 'markdown' }
      '''
        
    * index.html
    '''
        <!DOCTYPE html>
        <html>
        <head>
            <meta charset="utf-8" />
            <meta name="viewport" content="width=device-width, initial-scale=1.0" />
            <title>Content Manager</title>
            <!-- Include the script that enables Netlify Identity on this page. -->
            <script src="https://identity.netlify.com/v1/netlify-identity-widget.js"></script>
        </head>
        <body>
            <!-- Include the script that builds the page and powers Decap CMS -->
            <script src="https://unpkg.com/decap-cms@^3.0.0/dist/decap-cms.js"></script>
        </body>
        </html>
    '''

3. aggiungere Widget per login netlify dentro partials/head per avere login da tutte le pagine del sito al url  "/admin"
'''
<script src="https://identity.netlify.com/v1/netlify-identity-widget.js"></script>
'''

4. Pubblicare il sito su netlify
5. Attivare Identity dentro site setting
    * Registration > Invite Only > Identity Tab link e aggiungere indirizzo mail del admin cms > confermare invito alla mail inserita
    * External providers > Google
    * Git Gatewat > Enable, altrimenti non sarà possibile autenticarsi correttamente
