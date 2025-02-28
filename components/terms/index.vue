<template>
    <div class="content">
        <CommunHeader title="Terms and Services" description="Web Site Terms and Conditions of Use" />
        <ContentTitleDescription v-for="(section, key) in paragraphs" :key="`section--${key}`" :title="section.title"
            :descriptions="section.descriptions" />
        <CommunButtonBackToTop text="Back to top" />
    </div>
</template>

<script setup lang="ts">

const paragraphs = [
    {
        title: "Introduction",
        descriptions: ["Welcome to Echoique.com, the premier destination for product reviews, insights, and expert opinions. At Echoique.com, we are committed to providing our users with in-depth analysis of various products, offering valuable insights to make informed purchasing decisions. By accessing and using our website located at www.Echoique.com, you agree to comply with and be bound by the following Terms and Conditions, which govern Echoique.com's relationship with you in connection with this website. Please read these Terms and Conditions carefully before using our site. If you have any questions, please feel free to contact us at privacy@Echoique.com."]
    },
    {
        title: "Acceptance of Terms",
        descriptions: ["By accessing and using Echoique.com, you accept and agree to be legally bound by these Terms and Conditions, as well as our Privacy Policy, which can be found at [link to Privacy Policy]. If you disagree with any part of these terms, please refrain from using our website. Your continued access or use of Echoique.com after any revisions to these Terms and Conditions will constitute your acceptance of the changes. If you do not understand or have any questions regarding these Terms and Conditions, please contact us at privacy@Echoique.com, and we will be happy to assist you."]
    },
    {
        title: "Changes to Terms",
        descriptions: ["Echoique.com reserves the right, in our sole discretion, to revise and update these Terms and Conditions at any time. Any changes are effective immediately upon posting to the site, and apply to all access to and use of the site thereafter. Your continued use of the site following the posting of revised Terms and Conditions means that you accept and agree to the changes. As such, it is your responsibility to check this page periodically for updates. The date of the latest update to these Terms and Conditions will be indicated at the top of this page."]
    },
    {
        title: "Access and Use of the Site",
        descriptions: ["Access to www.Echoique.com is granted to all users who are at least [appropriate age, for example, 18] years old. Our website is designed to provide product reviews and expert opinions to assist you in making informed purchasing decisions. The content, information, and services provided through our website are intended for personal, non-commercial use only.",
            "Users are prohibited from using the site and its services for any unlawful purpose or in any way that could damage, disable, overburden, or impair the availability or functionality of the site. Users are also prohibited from attempting to gain unauthorized access to the site, or any networks connected to the site, by any means.",
            "In order to maintain the safety and integrity of our website, we reserve the right to monitor the use of the site. www.Echoique.com reserves the right to refuse access to the site, or to remove or edit any content, at our sole discretion for any reason, including but not limited to situations where user conduct violates applicable laws or is harmful to the interests of www.Echoique.com and its affiliates.",
            "Moreover, www.Echoique.com is not responsible for the availability or content of other services that may be linked to our website. When you access third-party websites or use third-party services, you accept that there are risks in doing so and that www.Echoique.com is not responsible for such risks."]
    },
    {
        title: "User Obligations",
        descriptions: ["As a user of Echoique.com, you are entrusted with certain responsibilities and obligations to maintain an environment that is safe, respectful, and beneficial to all other users. To that end, you agree to abide by the following conditions:",
            "Lawful Use: You will only use our website for lawful purposes, in compliance with all applicable local, national, and international laws and regulations. This includes, but is not limited to, laws pertaining to copyright and intellectual property, defamation, privacy, and the transmission of technical data exported from your country of residence.",
            "Prohibited Activities: You agree not to engage in activities that compromise the security of the website or attempt to gain unauthorized access to the underlying technology of the site. This includes, but is not limited to, activities such as hacking, password mining, or other attempts to discover the source code of the site.",
            "Integrity of the Site: You will not upload, post, transmit, distribute, or otherwise make available any content that contains software viruses or any other computer code, files, or programs designed to interrupt, destroy, or limit the functionality of the website, other users’ access to the website, or the underlying software.",
            "Respectful Conduct: You agree not to intimidate, harass, mock, or otherwise engage in conduct that negatively affects other users' experience of the site. This includes any activity that may be considered obscene, defamatory, or discriminatory.",
            "Spamming: The use of the website for the creation, sending, or display of unsolicited bulk communications, advertising, or promotional material, or any other form of unauthorized solicitation to any third party, is strictly prohibited.",
            "Violations of these user obligations may lead to suspension or termination of your access to the website, at the sole discretion of Echoique.com."]
    },
    {
        title: "Intellectual Property",
        descriptions: ["All intellectual property rights in the website, its design, and all materials on or accessible through the website are owned by Echoique.com or its licensors. These rights include, but are not limited to, ownership of all text, graphics, images, logos, copyrighted material, trademarks, patents, software, and other distinctive brand features displayed on the site.",
            "The compilation of all content on the website is the exclusive property of Echoique.com and is likewise protected by copyright and other intellectual property laws. Unauthorized use of this content may violate these laws and could result in legal action.",
            "As a user, you are permitted to access the site and its contents for your personal and non-commercial use. No portion of the website may be reproduced, duplicated, copied, sold, resold, or otherwise exploited for any commercial purpose without express written consent from Echoique.com.",
            "You are prohibited from using any of the marks or logos appearing throughout the site without express permission from the trademark owner, except as permitted by applicable law. You agree not to alter, obscure, or remove any copyright, trademark, or any other notices that appear on the website.",
            "In accessing the website and its content, you agree to do so only in a way that is consistent with these terms and the rights of third parties, and in compliance with applicable laws and regulations."]
    },
    {
        title: "Affiliate Disclosure",
        descriptions: ["At Echoique.com, we believe in full transparency. This is why we want to make it clear that we have incorporated affiliate links into our website. These are links to products or services, which, if you click on them and make a purchase, Echoique.com will receive a small commission at no extra cost to you.",
            "These affiliate commissions are what help us keep Echoique.com running, allowing us to continue providing you with high-quality product reviews and expert insights. We participate in various affiliate marketing programs, which means we may get paid commissions on chosen products purchased through our links to retailer sites.",
            "Please note that these affiliate partnerships do not influence the products we review or the ratings we give. Each product is evaluated independently, and the views and opinions expressed on our site are strictly our own. We always strive to provide honest, unbiased reviews to help you make informed purchasing decisions.",
            "Our affiliations include, but are not limited to, the [Affiliate Program Name(s)]. However, we do not accept money, services, or any other forms of payment in exchange for endorsements or mentions. All of our reviews are based on thorough research and, where possible, hands-on testing.",
            "By using the affiliate links on our site, you are supporting Echoique.com, and we genuinely appreciate your patronage. However, we understand that not everyone will want to use these links. Should you choose to use them, we thank you for your support!"]
    },
    {
        title: "Product Reviews and Rankings",
        descriptions: ["Echoique.com provides expert reviews and comparisons of various products to help you make informed purchasing decisions. The selection of products reviewed on our site are carefully chosen based on their relevance, popularity, and quality.",
            "We maintain a rigorous process for examining products. This includes researching product details, consulting user reviews and industry experts, and, when possible, hands-on testing. Our primary goal is to provide a balanced and reliable source of information.",
            "Please note that some of the products on our site are linked to businesses that provide us with compensation, or in which we have a vested interest. This could affect the way in which these products are displayed on our site, including the order in which they appear. However, such considerations do not influence our evaluation of the products.",
            "Product rankings can change based on a variety of factors, including the user's device, location, date, time, cookie data, and any other data generated on this site. Not all available products in a specific category are included in our rankings.",
            "Our rankings and reviews are generated from our own perspectives, understandings, and beliefs. It's important to note that we do not evaluate every available product within a specific category, and the opinions shared on our platform are solely our own.",
            "In order to offer free comparisons and keep the website running, we receive referral commissions from some of the companies whose products are featured and analyzed on our website. Despite this, we strive to remain impartial and offer fair, unbiased reviews. These commissions in no way affect our recommendations or influence the integrity of our reviews."]
    },
    {
        title: "Limitations of Liability and Disclaimers",
        descriptions: ["Echoique.com provides this website and its content on an \"as is\" and \"as available\" basis. We make no representations or warranties of any kind, express or implied, as to the operation of this website, or the information, content, materials, products, or services included on or associated with this site.",
            "To the fullest extent permissible by applicable law, Echoique.com disclaims all warranties, express or implied, including but not limited to, implied warranties of merchantability, fitness for a particular purpose, non-infringement, and other violations of rights.",
            "We do not warrant that the information, content, materials, products, or other services provided by this website are accurate, reliable, complete, or error-free, or that the website, its servers, or emails sent from Echoique.com are free of viruses or other harmful components.",
            "In no event shall Echoique.com, its directors, officers, employees, affiliates, agents, contractors, interns, suppliers, service providers, or licensors be liable for any injury, loss, claim, or any direct, indirect, incidental, punitive, special, or consequential damages of any kind, including, without limitation, lost profits, lost revenue, lost savings, loss of data, replacement costs, or any similar damages, whether based in contract, tort (including negligence), strict liability, or otherwise, arising from your use of the website or any products procured using the site, or for any other claim related in any way to your use of the site or any product.",
            "The above limitations apply even if Echoique.com has been advised of the possibility of such damages. Because some states or jurisdictions do not allow the exclusion or limitation of liability for consequential or incidental damages, in such states or jurisdictions, our liability shall be limited to the maximum extent permitted by law.",
            "Your use of, or inability to use, the service is at your sole risk. The service and all products and services delivered to you through the service are (except as expressly stated by us) provided 'as is' and 'as available' for your use, without any representation, warranties, or conditions of any kind, either express or implied.r your use, without any representation, warranties, or conditions of any kind, either express or implied."]
    },
    {
        title: "Indemnification",
        descriptions: ["You agree to indemnify, defend, and hold harmless Echoique.com, its subsidiaries, affiliates, partners, officers, directors, agents, contractors, licensors, service providers, subcontractors, suppliers, interns, and employees, from any claim or demand, including reasonable attorneys' fees, made by any third-party due to or arising out of your breach of these Terms and Conditions, or your violation of any law or the rights of a third-party.",
            "Your agreement to indemnify Echoique.com means that you agree to protect us, pay for, or reimburse any costs (including, but not limited to, damages awarded against us, our legal fees, and costs) if we are sued or incur any losses because of something you did or something you are responsible for.",
            "This obligation applies whether the claim or demand arises out of contract, tort, or statute. You will cooperate as fully required by Echoique.com in the defense of any claim. Echoique.com reserves the right, at its own expense, to assume the exclusive defense and control of any matter otherwise subject to indemnification by you, and you must not settle any matter without the written consent of Echoique.com.",
            "This indemnification section survives the termination of these Terms and Conditions and your use of the Echoique.com site. If you cause a technical disruption of the site or the systems transmitting the site to you or others, you agree to be responsible for any and all liabilities, costs, and expenses (including attorneys' fees) arising from that disruption."]
    },
    {
        title: "Termination",
        descriptions: ["Echoique.com reserves the right, in its sole discretion, to terminate your access to the website and the related services or any portion thereof at any time, without notice.",
            "We may terminate or suspend your access to our site immediately, without prior notice or liability, for any reason whatsoever, including without limitation if you breach these Terms and Conditions. Upon termination of your access, your right to use the website will immediately cease.",
            "We also reserve the right to remove or delete any information that you have provided to us, including any account or login information. However, obligations and liabilities incurred by you before the termination date will survive the termination of this agreement for all purposes.",
            "Moreover, we may discontinue the website and its services, or your use of the website and its services, with or without notice to you. We will not be liable to you or any third-party should we exercise our right to modify or discontinue the website.",
            "Please note that we have the ability to terminate your access without providing reasons. We may also change, suspend, or discontinue all or any aspect of the website at any time, including the availability of any feature or content without prior notice or liability."]
    },
    {
        title: "Governing Law and Jurisdiction",
        descriptions: ["These Terms and Conditions, and any separate agreements through which we provide services to you, shall be governed by, construed, and enforced in accordance with the laws of Spain. All matters relating to the interpretation, validity, and performance of these Terms and Conditions shall be determined under the laws of Spain. The parties agree to submit to the exclusive jurisdiction of the courts of Spain for the resolution of any disputes or claims arising out of or relating to these Terms and Conditions."]
    },
    {
        title: "Contact Information",
        descriptions: ["If you have any questions or concerns regarding these Terms and Conditions, we encourage you to contact us via email. We value our users and will endeavor to address your inquiries as promptly as possible.", "Please reach us at:", "Email: privacy@Echoique.com"]
    }
]

</script>

<style scoped lang="scss">
.content {
    display: flex;
    flex-direction: column;
    gap: 30px;
    margin: auto;
}
</style>