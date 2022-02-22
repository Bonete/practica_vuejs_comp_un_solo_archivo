<template>
    <div>
        <!-- TODO: Crear componente GitHub -->
        <input v-model="user" placeholder="Introduce nombre de usuario de GitHub"  v-on:keydown="obtenerUsuario"/>
    </div>
</template>

<script>

// TODO: Importar componente GitHubRepos
import GitHubRepos from 'GitHubRepos.vue'

export default {
    name: 'GitHub',
    components: {
        // TODO: Importar componente GitHubRepos
        GitHubRepos
    },
    data: function() {
        return {
            // TODO: crear variables de datos para el funcionamiento del componente
        }
    },
    methods: {
        obtenerUsuario: function() {
            // TODO: Función para obtener los datos de usuario de la API de GitHub

            // TODO: Añadir lógica para resetear los cambios en el interfaz: desactivar campo de envío,
            // resetear mensaje de error, mostrar lista de repositorios,...

            // Obtener datos de autenticación de usuario para hacer peticiones
            // autenticadas a la API de GitHub
            var userAuth = process.env.VUE_APP_USERNAME || "Bonete";
            var passAuth = process.env.VUE_APP_USERTOKEN || "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";

            // TODO: realizar petición fetch par obtener los datos y mostrar la información en la página
            // Ejemplo de paso de datos de autorización con fetch: https://stackoverflow.com/questions/43842793/basic-authentication-with-fetch
            let url = 'https://api.github.com/users/{{user}} ';
            fetch(url,{method:'GET'})
            .then(response => response.json())
            .then(data => {
              const login = data.login;
              const avatar = data.avatar_url;
              const html_url = data.html_url;
              const repos_url = data.repos_url;
            });

        },
        obtenerRepositorios: function() {
            // TODO: Función para obtener los repositorios del usuario desde la API de GítHub
            // La URL de los repositorios de usuario se puede obtener a través del campo 'repos_url' de los datos del usuario

            // Obtener datos de autenticación de usuario para hacer peticiones
            // autenticadas a la API de GitHub
            var userAuth = process.env.VUE_APP_USERNAME || "Bonete";
            var passAuth = process.env.VUE_APP_USERTOKEN || "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";


            // TODO: realizar petición fetch par obtener los datos y mostrar la información en la página
            // Ejemplo de paso de datos de autorización con fetch: https://stackoverflow.com/questions/43842793/basic-authentication-with-fetch
                        let url = 'https://api.github.com/users/{{user}}/repos';
            fetch (url,{method:'GET'})
            .then(response => response.json())
            .then(data => {
            const full_name = data.full_name;
            const html_url = data.html_url;
            const description = data.description;
            const forks_count = data.forks_count;
            });

        }
    }
}
</script>

<style scoped>
</style>
