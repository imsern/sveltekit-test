
<script>
    import emailjs from 'emailjs-com';

    const serviceId = 'your_service_id';  // Replace with your EmailJS service ID
    const templateId = 'your_template_id'; // Replace with your EmailJS template ID
    const publicKey = 'your_public_key';   // Replace with your EmailJS public key

    let formData = {
        name: '',
       email: '',
       message: ''
   };

   async function sendEmail() {
       try {
           await emailjs.send(serviceId, templateId, formData, publicKey);
           alert('Message sent successfully!');
           formData = { name: '', email: '', message: '' };
       } catch (error) {
           console.error('Failed to send message:', error);
           alert('Failed to send message. Please try again.');
       }
   }
</script>
<main class="flex flex-col items-center p-8 bg-black min-h-screen">
    <h1 class="text-3xl text-orange-500 font-bold mb-4">Contact Me</h1>
    <p class="mb-8 text-gray-500">
        I’d love to hear from you! Use the form below to get in touch.
    </p>

<form class="bg-gray-900 p-6 shadow-md rounded-lg w-full max-w-md space-y-4 flex flex-col" on:submit|preventDefault={sendEmail}>
        <div>
            <label class="label">
                <span class="label-text text-orange-500">Your Name</span>
            </label>
            <input type="text" placeholder="Enter your name" bind:value={formData.name} class="input input-bordered w-full bg-gray-800 text-white placeholder-gray-400" />
        </div>

        <div>
            <label class="label">
                <span class="label-text text-orange-500">Your Email</span>
            </label>
            <input type="email" placeholder="Enter your email" bind:value={formData.email} class="input input-bordered w-full bg-gray-800 text-white placeholder-gray-400" />
        </div>

        <div>
            <label class="label">
                <span class="label-text text-orange-500">Your Message</span>
            </label>
            <textarea
                    placeholder="Write your message"
                    bind:value={formData.message} class="textarea textarea-bordered w-full bg-gray-800 text-white placeholder-gray-400"
            ></textarea>
        </div>

        <button type="submit" class="btn bg-orange-500 hover:bg-orange-400 text-white w-full md:w-auto self-end">Send Message</button>
    </form>
</main>
