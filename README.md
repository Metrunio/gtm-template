# Metrunio Tracking: Google Tag Manager template

Loads the Metrunio tracker on your website through Google Tag Manager.

## Setup

1. In Google Tag Manager, add a new tag and pick **Metrunio Tracking** from the
   Community Template Gallery.
2. Enter the **Site ID** and **Write Key** from the Metrunio portal
   (Setup).
3. If you set up your own measurement domain in the portal, enter it under
   **Measurement domain**, for example `https://gauge.example.com`. Otherwise
   leave it empty.
4. Under **Consent tool**, pick your consent tool if Metrunio has a bridge
   for it (Usercentrics, Cookiebot, consentmanager, OneTrust and others).
   The tag then loads the bridge, which takes the decision from that tool.
5. Tick the consent boxes only if the tag's trigger fires after the visitor
   has consented. If both stay empty, the tag reports no decision: Metrunio
   waits until your consent tool reports one through `metrunio.setConsent`
   and sends nothing until then.
6. Publish the container.

## Leads, goal steps and purchases

Add a second tag from the same template and set **Tag type** to
**Conversion**. Pick the conversion type:

- **Goal step**: the key of the step, for example `signed_up`, and
  optionally your customer ID. The tag reports the customer ID first.
- **Lead**: optionally the lead ID, the value and the currency.
- **Purchase**: the order number (required), the value and the currency.

Every field takes a GTM variable, for example a data layer variable. Fire the
tag on the event that marks the action, and in **Tag sequencing** fire the
base tag before it.

A conversion without a consent decision is dropped, not held back. The
preview console says so and names the ways out: fire the tag after the
action and the decision, sequence it after the base tag, or report the
conversion from your server.

The script and the bridge always load from `collect.metrunio.com`. To load the script from your own
measurement domain as well, import the template file offered in the Metrunio
portal instead of this gallery template.

Documentation: https://metrunio.com/en/help/gtm-verbinden

## License

Apache License 2.0, see `LICENSE`.
