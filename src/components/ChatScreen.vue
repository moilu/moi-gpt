<template>
    <div>
        <p>
            ¿Puedes enseñarme a escribir canciones y si no puedes, pudieras dirigirme a algun recurso?
        </p>
        <br>
        <p v-if="aiData">
            {{ aiData.choices[0].text }}
        </p>
    </div>
</template>
<script>
export default {
    name: 'ChatScreen',
    data() {
        return {
            aiData: {},
            apiKey: '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'
        }
    },
    methods: {
         getOpenAI() {
            fetch('https://api.openai.com/v1/completions', {
                method: 'POST',
                headers: {
                    'Accept': 'application/json',
                    'Content-Type': 'application/json',
                    'Authorization': `Bearer ${this.apiKey}`
                },
                body: JSON.stringify({
                    "model": "text-davinci-003",
                    "prompt": "You are a helpful asistant. ¿Puedes enseñarme a escribir canciones y si no puedes, pudieras dirigirme a algun recurso?",
                    "temperature": 0,
                    "max_tokens": 100,
                    "top_p": 1,
                    "frequency_penalty": 0.0,
                    "presence_penalty": 0.0,
                })
            })
            .then((resp) => resp.json())
            .then((data) => {
                this.aiData = data;
                console.log(data);
            });
        }
    },
    mounted() {
        this.getOpenAI();
    },
}
</script>