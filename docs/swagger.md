<div id="swagger-ui"></div>

  <script>
    // window.onload = function() {
    function load() {
      console.log('WINDOW ONLOAD!')
      const ui = SwaggerUIBundle({
        url: "https://raw.githubusercontent.com/Cinebody/cinebody-api-app-schema/master/src/schema.yaml",
        dom_id: '#swagger-ui',
        presets: [
          SwaggerUIBundle.presets.apis,
          SwaggerUIStandalonePreset
        ]
      })

      window.ui = ui
    }
	setTimeout(() => {
		load()
	}, 50)
</script>
