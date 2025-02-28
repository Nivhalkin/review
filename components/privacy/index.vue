<template>
    <div class="content">
        <CommunHeader title="Privacy Policy"
            description="This Privacy Policy describes Our policies and procedures on the collection, use and disclosure of Your information when You use the Service and tells You about Your privacy rights and how the law protects You. We use Your Personal data to provide and improve the Service. By using the Service, You agree to the collection and use of information in accordance with this Privacy Policy." />
        <template v-for="(section, key) in paragraphs" :key="`section--${key}`">
            <template v-if="section.type === 1">
                <ContentTitleDescription :title="section.title" :descriptions="section.descriptions" />
            </template>
            <template v-if="section.type === 2">
                <CommunTitleSubTitleList :title="section.title" :subSection="section.subSection" />
            </template>
        </template>
        <CommunButtonBackToTop text="Back to top" />
    </div>
</template>

<script setup lang="ts">

const paragraphs = [
    {
        type: 1,
        title: "Interpretation",
        descriptions: ["The words of which the initial letter is capitalized have meanings defined under the following conditions.The following definitions shall have the same meaning regardless of whether they appear in the singular or in the plural.",
            "What information do we collect? When you visit our Website you may provide us with two types of information: personal information you knowingly choose to disclose that is collected on an individual basis and Website use information collected for general data purposes as you and others browse our Website."]
    },
    {
        type: 1,
        title: "Definitions",
        descriptions: ["The definitions used in this Policy are as follows:", "\"Data Subject\" or \"You\": Refers to any natural person accessing or utilizing our Services, including a company, or other legal entities on whose behalf such individual is accessing or using the Services. This term applies universally to all visitors and customers.",
            "\"Company\": Refers to Kinai Media Sl., a legal entity duly registered under the laws of Spain, having its registered office at Calle Muntaner, 371 - P. 4 PTA. 1, Barcelona, 08021, Barcelona. The Company operates the website Echoique.com and its respective subdomains.",
            "\"Affiliate\": Refers to an entity that directly or indirectly controls, is controlled by, or is under common control with a party, where \"control\" implies the ownership of more than 50% of voting rights.",
            "\"Account\": Denotes a unique identifier created by the Data Subject to access our Services or parts thereof.",
            "\"Website\": Refers to the primary online presence of the Company, accessible from [Your Website URL], offering our products and services.",
            "\"Services`\": Denotes the comprehensive suite of products, recommendations, insights, evaluations, and user reviews offered by the Company through any platform or medium.",
            "\"Country\": Refers to Spain, being the jurisdiction where the Company is incorporated and primarily operates.",
            "\"Service Provider\": Denotes any individual or legal entity assigned by the Company to process data. This term encompasses third-party businesses or individuals commissioned by the Company to enable the Service, represent the Company in service provision, deliver services associated with the Service, or aid the Company in understanding Service usage.",
            "\"Third-Party Social Media Service\": Represents any platform or social network website where a User can log in or create an account to avail the Services.",
            "\"Personal Data\": Denotes any information relating to an identified or identifiable natural person.",
            "\"CCPA\": Refers to the California Consumer Privacy Act, a state statute of the United States designed to enhance privacy rights and consumer protection for residents of California.",
            "\"Cookies\": Refers to small data files placed on your device by a website, storing the details of your browsing history on that website among its various uses.",
            "\"Usage Data\": Pertains to data that is automatically collected, either produced by the use of the Service or from the Service infrastructure itself (such as the duration of a page visit).",
            "\"Do Not Track (DNT)\": Represents a concept endorsed by U.S. regulatory bodies, notably the U.S. Federal Trade Commission (FTC), calling for the development and implementation of a mechanism enabling internet users to manage the tracking of their online activities across websites.",
            "\"Business\": In the context of the CCPA (California Consumer Privacy Act), this term designates the Company as the legal entity gathering Consumers' personal data, dictating the purposes and means of processing such data, or for which such data is gathered, and determining, solely or jointly with others, the purposes and means of processing consumers' personal data while conducting business in California.",
            "\"Consumer\": As per the CCPA (California Consumer Privacy Act), signifies a natural person who is a resident of California. As the law defines, a resident includes (1) every individual in the USA for other than a temporary or transitory purpose, and (2) every individual domiciled in the USA who is outside the USA for a temporary or transitory purpose.",
            "\"Sale\": In accordance with the CCPA (California Consumer Privacy Act), this term denotes the act of selling, renting, releasing, disclosing, disseminating, making available, transferring, or otherwise communicating, whether orally, in writing, or by electronic or other means, a Consumer's Personal Information to another business or a third party in exchange for monetary or other valuable consideration.",
            "\"Collecting and Using Your Personal Data\": Refers to the process by which the Company gathers and utilizes your personal data in accordance with the terms outlined in this Privacy Policy."]
    },
    {
        type: 2,
        title: "Gathering and Utilizing Your Personal Information",
        subSection: [
            {
                title: "Identifiable Information",
                descriptions: ["During your interaction with our Service, we might request you to share specific personal details that can assist us in communicating with or recognizing you. This personal identifiable information can consist of, but is not restricted to:"],
                list: ["Your email address", "Your first and last name", "Contact number", "Residential details including state, province, ZIP / postal code, and city"]
            },
            {
                title: "Data Related to Usage",
                descriptions: ["The usage-related data is procured automatically during the utilization of our Service.",
                    "It could comprise details such as your device's Internet Protocol address (IP address), the type and version of your browser, the sections of our Service that you browse, the exact time and date of your access, the duration of your stay on these pages, unique device identification elements, and other diagnostic data."],
            },
            {
                title: "Use of Tracking Elements and Cookies",
                descriptions: ["We utilize Cookies and analogous tracking tools to monitor interactions on Our Service and to save certain types of information. The tracking tools employed include beacons, tags, and scripts that help in gathering and tracking details, and contribute to the improvement and analysis of our Service.",
                    "You have the option to configure your browser to decline all Cookies or to notify you when a Cookie is being dispatched. Please note, if you choose not to accept Cookies, you may be unable to access certain portions of our Service.",
                    "Cookies can either be \"Persistent\" or \"Session\" type. Persistent Cookies stay on your computer or mobile device even after you go offline, while Session Cookies are removed the moment you close your web browser."],
            },
        ]
    },
    {
        type: 2,
        title: "We utilize both session and persistent Cookies for the below-listed purposes",
        subSection: [
            {
                title: "Essential Cookies",
                descriptions: ["Objective: These Cookies are crucial to avail the services offered through the Website and to utilize some of its functionalities. They assist in verifying users and preventing fraudulent activities on user accounts. Without these Cookies, the services you have requested cannot be delivered, and we only employ these Cookies to furnish you with those services."],
            },
            {
                title: "Cookies Policy/Notice Consent Cookies",
                descriptions: ["These Cookies help determine if users have consented to the use of cookies on the Website."],
            },
            {
                title: "Functional Cookies:",
                descriptions: [" These Cookies facilitate us in remembering the choices you make when you utilize the Website, such as retaining your login information or language preference. The aim of these Cookies is to provide you with a more customized experience and to prevent the necessity of re-entering your preferences each time you utilize the Website."],
            },
            {
                title: "Performance and Tracking Cookies:",
                descriptions: ["These Cookies help track details about traffic directed to the Website and how users interact with the Website. The information obtained via these Cookies may directly or indirectly identify you as a distinct visitor. This is because the information collected is usually linked to a pseudonymous identifier associated with the device you use to access the Website. We may also use these Cookies to trial new ads, pages, features, or new functionalities of the Website to evaluate our users' responses to them."],
            },
        ]
    },
    {
        type: 2,
        title: "Your Personal Data Utilization",
        subSection: [
            {
                title: "Our Company may employ Personal Data in accordance with the following objectives",
                descriptions: ["To deliver and uphold our Service, inclusive of observing the usage of our Service.",
                    "Account Management: Handling your registration as a Service user. The Personal Data you share can grant you access to various Service features exclusive to registered users.",
                    "Contract Performance: The formulation, adherence, and execution of the purchase agreement for the goods, items, or services you've acquired, or any other agreement with us through the Service.",
                    "Communication: Reaching out to you via email, phone calls, SMS, or other similar electronic communication methods such as push notifications from a mobile app, pertaining to updates or informational communications connected to the features, products, or services contracted, inclusive of security updates, as and when required or reasonable for their execution.",
                    "Updates and Offers: Supplying you with updates, exclusive offers, and general details about other products, services, and events that we provide that are akin to those you've previously purchased or asked about, unless you've chosen not to receive such information.",
                    "Request Management: Responding to and managing your requests directed to us."],
            },
            {
                title: "The scenarios in which we might disseminate your personal information are as follows",
                descriptions: ["In Collaboration with Service Providers: Your personal data may be shared with Service Providers for purposes such as monitoring and analyzing the usage of our Service, presenting advertisements to you to aid in the support and upkeep of our Service, for getting in touch with you, to display ads on third-party websites to you following your visit to our Service, or for payment processing.",
                    "In Business Transactions: We may transfer or share your personal information in association with, or during the discussions of, any merger, the sale of Company assets, financing, or the acquisition of all or a portion of our enterprise by another company.",
                    "With Affiliates: Your information could be shared with our Affiliates, under which circumstances we will necessitate those Affiliates to respect this Privacy Policy. Affiliates encompass our parent company and any other subsidiaries, joint venture partners, or other companies that we either control or are under shared control with us.",
                    "With Business Allies: We may distribute your information with our Business associates to present to you specific products, services, or promotional offers.",
                    "With Other Users: When you disclose personal data or engage in public areas with other users, such information might be viewable by all users and could be publicly distributed beyond. If you interact with other users or sign up via a Third-Party Social Media Service, your contacts on the Third-Party Social Media Service might see your name, profile, images, and a summary of your activities. Similarly, other users will have the capability to view summaries of your activity, communicate with you, and view your profile.",
                    "Maintaining Your Personal Data: We will store your Personal Data only for the time necessary for the intentions outlined in this Privacy Policy. Your Personal Data will be kept and utilized to the degree needed to meet our legal commitments (for instance, if we are mandated to keep your data in compliance with relevant laws), settle disputes, and enforce our legal contracts and guidelines.We will also keep Usage Data for internal assessment objectives. Usage Data is usually kept for a shorter duration, unless this data is employed to augment the security or enhance the functionality of our Service, or we are legally bound to keep this data for longer periods.",
                    "Relocation of Your Personal Data: Your details, which include Personal Data, are processed at the company's functional offices and at any other places where the entities involved in processing are based. This implies that your data could be transferred to — and held on — computers positioned outside of your state, province, country, or other governmental jurisdiction where the laws safeguarding data may differ from those in your jurisdiction.Your consent to this Privacy Policy followed by your provision of such information indicates your acceptance of that transfer. We will undertake all reasonable measures to ensure that your data is handled securely and in alignment with this Privacy Policy, and no transfer of your Personal Data will occur to an organization or a country unless there are sufficient safeguards in place, including the security of your data and other personal details.",
                    "Revealing Your Personal Data, Business Activities: If the Company is engaged in a merger, acquisition, or asset sale, your Personal Data could be transferred. We will offer notification before your Personal Data is transferred and falls under a different Privacy Policy."
                ],
            },
        ]
    },
    {
        type: 1,
        title: "Law Enforcement Involvement",
        descriptions: ["In certain situations, we may be obliged to disclose your Personal Data if it's required by law or in response to legitimate requests from public authorities (like a court or a government agency).r web browser."]
    },
    {
        type: 2,
        title: "Additional Legal Requirements",
        subSection: [
            {
                descriptions: ["Your Personal Data may be disclosed by us if we sincerely believe that such action is needed to:"],
            },
            {
                title: "The scenarios in which we might disseminate your personal information are as follows",
                list: ["Adhere to a legal commitment",
                    "Safeguard and defend the Company's rights or property",
                    "Investigate or prevent potential misconduct related to the Service",
                    "Ensure the personal safety of the Service users or the general public",
                    "Shield against legal accountability"],
            },
        ]
    },
    {
        type: 1,
        title: "Securing Your Personal Data",
        descriptions: ["The protection of your Personal Data is crucial to us, but remember, no method of data transmission over the Internet or electronic storage technique is entirely foolproof. While we make every effort to use commercially viable means to secure your Personal Data, we cannot assure its absolute safety.",
            "In-depth Information on Your Personal Data Processing. Service Providers can access your Personal Data solely to perform tasks on our behalf and are obligated not to disclose or utilize it for any other intention."]
    },
    {
        type: 1,
        title: "Analytics",
        descriptions: ["We might utilize third-party Service providers to observe and analyze the utilization of our Service.",
            "Google Analytics, a web analytics service provided by Google, tracks and reports on website traffic. Google uses the collected data to track and monitor our Service usage. This data is shared with other Google services. Google might use the gathered data to contextualize and personalize the advertisements of its own ad network.You have the option to opt-out of sharing your activity on the Service with Google Analytics by installing the Google Analytics opt-out browser add-on. This add-on prevents the Google Analytics JavaScript (ga.js, analytics.js, and dc.js) from sharing visit activity information with Google Analytics.For more details on Google's privacy practices, please visit the Google Privacy & Terms webpage: https://policies.google.com/privacy?hl=en.",
            "Our Company employs remarketing strategies to advertise on third-party websites to you once you have visited our Service. Both we and our third-party vendors utilize cookies to inform, optimize, and serve advertisements based on your previous interactions with our Service.",
            "Facebook's remarketing service is facilitated by Facebook Inc. To learn more about Facebook's interest-based advertising, visit: https://www.facebook.com/help/1649686938371024. To opt out of Facebook's interest-based ads, adhere to these guidelines from Facebook: https://www.facebook.com/help/568137493302217. Facebook complies with the Self-Regulatory Principles for Online Behavioral Advertising established by the Digital Advertising Alliance. You can also opt out from Facebook and other participating companies via the Digital Advertising Alliance in the USA at http://www.aboutads.info/choices/, the Digital Advertising Alliance of Canada in Canada at http://youradchoices.ca/, or the European Interactive Digital Advertising Alliance in Europe at http://www.youronlinechoices.eu/, or by using your mobile device settings.To gain more insight into Facebook's privacy practices, visit Facebook's Data Policy: https://www.facebook.com/privacy/explanation"]
    },
    {
        type: 2,
        title: "Your Rights under the CCPA",
        subSection: [
            {
                descriptions: ["Notification Right - We are obligated to inform you of the type of Personal Data we collect and the reasons behind collecting this data.",
                    "Access and Request Right - According to the CCPA, you are entitled to ask and receive information from our Company regarding the disclosure of your Personal Data that we or our subsidiaries have collected over the past 12 months and disclosed to a third-party for direct marketing purposes.",
                    "Right to Refuse Personal Data Sales - You possess the right to instruct us not to sell your Personal Data to third parties. To enact this right, please visit our “Opt Out of Personal Data Sales” section or web page.",
                    "Right to Personal Data Disclosure - You are entitled to request and receive from our Company details about the following:"
                ],
                list: ["Adhere to a legal commitment",
                    "Safeguard and defend the Company's rights or property",
                    "Investigate or prevent potential misconduct related to the Service",
                    "Ensure the personal safety of the Service users or the general public",
                    "Shield against legal accountability"],
            },
            {
                descriptions: ["Personal Data Deletion Right - You possess the right to request the elimination of your Personal Data that we have collected over the past 12 months.",
                    "Anti-Discrimination Right - You are entitled to exercise your consumer rights without facing discrimination, which includes but is not limited to:"],
                list: ["Denial of goods or services to you",
                    "Imposition of varying prices or rates for goods or services, including the application of discounts or other benefits or penalties",
                    "Provision of a varying level or quality of goods or services to you",
                    "Suggestion that you will receive a varying price or rate for goods or services, or a varying level or quality of goods or services."]
            },
        ]
    },
    {
        type: 2,
        title: "Enacting Your CCPA Data Protection Privileges",
        subSection: [
            {
                descriptions: ["As a resident of California, you have the opportunity to utilize your CCPA-granted rights. To initiate this process, email us at privacy@echoique.com",
                    "Upon receipt of your verifiable request, we will disclose and deliver the pertinent information, free of charge, within 45 days. If necessary, this time period may be extended by an additional 45 days once, given reasonable cause and prior notification.",
                    "Opting Out of Personal Information Sales",
                    "We do not engage in the sale of personal information. However, some of our Service Providers (for example, our advertising partners) might use technology within the Service that can be construed as selling personal information under CCPA law.",
                    "To opt out from the utilization of your personal information for interest-based advertising and these potential sales as dictated by the CCPA, follow the instructions below.",
                    "Please be aware that any opt-out will be browser-specific. You may need to enact the opt-out on all browsers that you use.",
                    "Opting Out On Our Website",
                    "You have the option to refuse the receipt of personalized ads served by our Service Providers by adhering to the instructions given on the Service:"],
                list: ["From our “Cookie Consent” notice banner",
                    "From our “CCPA Opt-out” notice banner",
                    "From our “Opt-Out of Personal Information Sales” notice banner",
                    "From our “Opt-Out of Personal Information Sales” link",
                    "This opt-out will store a cookie on your computer, unique to the browser you used for the opt-out. If you switch browsers or erase the cookies stored by your browser, you will need to opt out again."]
            },
        ]
    },
    {
        type: 2,
        title: "Mobile Device Settings",
        subSection: [
            {
                descriptions: ["Your mobile device provides capabilities to opt out of the use of app-related information for the delivery of targeted ads based on your interests:"],
                list: ["For Android devices, choose “Opt out of Interest-Based Ads” or “Opt out of Ads Personalization“",
                    "For iOS devices, enable “Limit Ad Tracking“",
                    "\"Do Not Track\" Policy as Mandated by California Online Privacy Protection Act (CalOPPA)",
                    "Our Service does not acknowledge Do Not Track signals. However, certain third-party websites track your browsing activities. If you visit such sites, you can adjust your web browser's preferences to communicate that you do not wish to be tracked. Enable or disable Do Not Track by visiting the preferences or settings page of your web browser."]
            },
        ]
    },
    {
        type: 1,
        title: "Protecting Children's Privacy",
        descriptions: ["Our Service is not intended for anyone under the age of 13. We do not knowingly gather personally identifiable information from individuals under 13. If you are a parent or guardian and realize your child has shared Personal Data with us, please contact us at privacy@echoique.com. If we learn that we have collected Personal Data from someone under 13 without parental consent verification, we will take steps to delete that information from our servers.",
            "We may restrict the way we collect, use, and store information from users between the ages of 13 and 18. Consequently, we may not provide certain service functionalities to these users.",
            "If consent is required as a legal basis for processing your data and your country mandates parental consent, we may require such consent from your parents before collecting and using that information."]
    },
    {
        type: 1,
        title: "Third-party Websites",
        descriptions: ["Our Service might include links to external websites not operated by us. Clicking a third-party link redirects you to the respective party's website. We highly recommend reviewing the Privacy Policy of each site you access.",
            "We have no influence over, and take no responsibility for, the content, privacy policies, or practices of any third-party sites or services."]
    },
    {
        type: 1,
        title: "Updates to Our Privacy Policy",
        descriptions: ["Our Privacy Policy may be updated occasionally. If any changes occur, we will notify you by posting the updated Privacy Policy on this page.",
            "We will inform you through email and/or a prominent notice on our Service, prior to the change becoming effective, and we'll update the \"Last updated\" date at the top of this Privacy Policy.",
            "We suggest you review this Privacy Policy from time to time for any modifications. Any changes to this Privacy Policy take effect as soon as they're posted on this page."]
    },
    {
        type: 1,
        title: "Get in Touch",
        descriptions: ["For any inquiries about this Privacy Policy, you can reach us:",
            "https://echoique.com/contact"]
    },
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