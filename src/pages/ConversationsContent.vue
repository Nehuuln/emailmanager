<template>
    <div>
      <button @click="$router.go(-1)">Retour</button>
      <h1>Conversation {{ getId }}</h1>
      <p>{{ conversationContent }}</p>
    </div>
  </template>
  
  <script>
  export default {
    name: "ConversationContent",
    props: 
    {id: (route) => ({ id: route.params.id })},
    data() {
      return {
        conversations: [
          { id: 1, title: 'Conversation 1', content: 'Content of conversation 1' },
          { id: 2, title: 'Conversation 2', content: 'Content of conversation 2' },
          { id: 3, title: 'Conversation 3', content: 'Content of conversation 3' },
        ]
      }
    },
    computed: {
      conversationContent() {
        const emails = JSON.parse(localStorage.getItem("emails"));
        for (let email of emails) {
          if (this.$route.params.id == email.id) {
          return email.message
        }
        }
        return "Empty message"
      },
      getId() {
        return this.$route.params.id
      }
    }
  }
  </script>