# VerifyGov

Let us begin with the proposition that:
- The fruit of one's labours should not be stolen by malefactors.

# Problem

Unfortunately in the current world we have scammers at large, preying on emotional vulnerabilities to extract money from their victims.

## Types of scams

The types of scams generally follow this categorization:
- Impersonation scams
- Investment scams
- Job scams
- Phishing scams
- E-commerce scams
- Love scams

Given the sheer variety of underlying reasons why people fall for these, we will simply be focusing on one particular type here, which are impersonation scams, particularly where scammers masquerade as government officials.

## The reason why these work

In cybersecurity, there's a concept known as Zero-Trust, where the main principle is:
- Never trust, always verify.

Unfortunately at this point in time, if someone claims to be a government official, what recourse does a regular citizen have to verify that the "official" is actually who they say they are?

Even if they present their "credentials", who's to say its real?

Even if it looks legitimate, there's always a chance that its simply a well made fake.

If you ask for a supervisor, they could simply call someone else involved in the scam to pose as their "supervisor".

There is simply no authorized, official manner of verifying an official's identity.

# Solution

There needs to be a simple, straightforward manner of verifying whether a person claiming to be a government employee is legitimate or not.
- This can potentially be rolled out to relevant industries such as banking, but let's table that for now.

## 1. Database

Let us first start by knowing that we will need to be able to verify whether a person is actually employed by the government.

To do this, there needs to be a database of government employees available for the system to check this.

There are two approaches we can go with for this:
1. Integrate with existing HR systems in the government
2. Have a new database with a list of officials AUTHORIZED to liaise with the general public for official purposes.

For the purposes of this project, integration with existing HR systems would likely be out of scope, as not all employees would need to be verified by the public as a government official.

Some could simply be doing administrative work that would not require them to interact with the public at large, leaving this functionality irrelevant for them.

To keep things lean and simple, each agency should simply submit a list of employees that are authorized and will likely need to be verified by the public. This can be reviewed on a regular basis.

## 2. Scenarios where verification is needed

This list might not be exhaustive, but the examples we will be using are:
1. Impersonation in person.
2. Impersonation via text, audio, or video calls.

Examples would be a "police officer" pressing you to transfer money or disclose banking details for an investigation.

## 3. Verification

To handle both scenarios, there needs to be multiple ways to verify whether the person you are in contact with is a legitimate government official, both face-to-face or remotely.

For a more familiar process to facilitate better understanding, we will be going with the scenario where the "official" is a "police officer".

### 3.1 Face-to-face

Given that:
1. There is a list of authorized government officials that liaises with the public.
2. To have a familiar process of a police officer showing their badge / credentials to "prove" that they are legitimate.
3. The ubiquity of Singpass and scanning QR codes to login to government websites.

We will introduce a QR code that is able to be scanned by the general public, which will check the officer's credentials against the list to verify that they are who they say they are.

This can be done either via a new dedicated VerifyGov app, or through the Singpass app itself to facilitate higher rollout rates to the general public.

The workflow would be as follows:
1. A dynamic QR code would be generated based on the officer's details, ensuring that a QR code can't be maliciously reused.
2. Upon scanning the QR code, there would be a request made to the backend service to verify that the officer exists in the database.
3. The result would then be reflected in the app.
4. In the event that the officer is legitimate, there should also be a record made to note that a particular citizen has scanned this officer's QR code to provide an interaction record which can be used for other purposes later on, such as to trim the list of officers in the database for those with low usage if necessary.

### 3.2 Remote

Since legitimate officers would typically know the identity of the person they are contacting in advance for investigations or follow-ups, they can utilize VerifyGov to provide a digital paper trail before/during the contact period.

The workflow would be as follows:
1. Pre-notification: Before an audio or video call takes place, the officer can log into the VerifyGov app and file an "Official Notice of Contact."
2. App Delivery: The citizen receives an automated notification within either their VerifyGov or Singpass Inbox.
3. The notice would contain:
    - The scheduled date and time of the contact.
    - The specific purpose of the call.
    - The officer’s name and official details such as their rank/role.
    - The citizen's details (to ensure the notice was sent to the correct recipient).
4. Verification: During the actual communication, the officer can state the details of the session, where the citizen can then cross-reference these verbal claims against the record app. If the details do not match, the citizen can immediately identify the call as fraudulent or erroneous.

## 4. Edge Cases & Limitations

### 4.1 No internet connectivity

To handle the event where there is a loss of internet connectivity on either the citizen's device or the backend service and the verification attempt is unable proceed normally, there can also be a signed digital certificate on the officer's device which can be scanned to show the officer's details as of the latest time it was updated.

However, as there is always the possibility of reverse engineering and spoofing, this record of "offline verification" should be stored locally on the citizen's device, and upon resumption of connectivity, a verification attempt should be made to the backend service to confirm that the officer was indeed legitimate.

In the event that they were a scammer, the citizen is at the very least notified and aware that they were tricked, and can proceed with reporting this to the authorities.

### 4.2 Theft of officer's device

In the situation, the officer will need to inform their superiors and in turn the VerifyGov staff that their device has been stolen, and the officer's record in the database can be updated to revoke their authorization.

# Conclusion

By implementing this ability to verify claims that a person is a government official, we move from a state of blind trust to a verify-first approach, ensuring that no scammers are able to masquerade as one.