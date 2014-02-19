#Demandbase / Optimizely Integration
This basic HTML file demonstrates how to use the [Demandbase JavaScript SDK](https://github.com/demandbaselabs/demandbaselabs/tree/master/JavaScriptSDK) with Optimizely.

This is a test.

There are two ways to use Demandbase within Optimizely.

1. Trigger an Optimizely Experiment based on a Demandbase Segment
2. Place a visitor in an Optimizely Visitor Segment based on a Demandbase Segment

#Prerequisites
1. Install the Optimizely tracking code as instructed in the 'Implementation' tab in Optimizely
2. Configure and install the [Demandbase JS SDK](https://github.com/demandbaselabs/demandbaselabs/tree/master/JavaScriptSDK)
  * Your Demandbase Solutions Consultant will assist you with this step.

#Trigger an Optimizely Experiment
Triggering an Optimizely Experiment using Demandbase allows you to personalize and target website content based on a visitor's company profile.
Multiple experiments can be setup and triggered according to various Demandbase Segments.  This works best when the Demandbase Segments do not overlap.

See [Visitor Condition Targeting](https://help.optimizely.com/hc/en-us/articles/200039685-Visitor-Condition-Targeting) for further detail on using Optimizely.

1. Create a new experiment with at least one variation
2. Under the Options menu, select **Targeting**, then select *Satisfy this custom JavaScript condition*.
  * Place a reference to a Demandbase Segment in the text box.  For example: `Demandbase.Segments.YourSegmentName`.
  * See your Demandbase code for your configured Demandbase Segments.
3. Set the [Activation Mode](https://help.optimizely.com/hc/en-us/articles/200039765-Activation-Mode) to *Manual*
4. Place the experiment activation code within the Demandbase `callback` function
  * Example:
  ```
  __db.callback = function(company) {
    window.optimizely = window.optimizely || [];
    window.optimizely.push(['activate', 'EXPT1_ID_HERE']);
    window.optimizely.push(['activate', 'EXPT2_ID_HERE']);
    window.optimizely.push(['activate', 'EXPTn_ID_HERE']);
  };
  ```
  *Note: the experiment ID is typically an integer, not a string.*
5. *Optional:* Adjust the [Traffic Allocation](https://help.optimizely.com/hc/en-us/articles/200040115-Traffic-Allocation) in Optimizely to use the variation more frequently.

#Create Optimizely Visitor Segments
Optimizely Visitor Segments allow you to dissect the results of an experiment based on visitor attributes.  This feature is only available in [Optimizely Platinum](https://www.optimizely.com/pricing).

See [Managing Visitor Segments from the Dashboard](https://help.optimizely.com/hc/en-us/articles/200040865-Managing-Visitor-Segments-from-the-Dashboard) for detailed instructions on how to setup Visitor Segments.

1. Create a new Visitor Segment.
2. Select *Satisfy this custom Javascript condition*
3. Place a reference to a Demandbase Segment in the text box.  For example: `Demandbase.Segments.YourSegmentName`.
  * See your Demandbase code for your configured Demandbase Segments.
4. To use your Visitor Segment, view the results of an experiment, then select your Custom Segment from the menu on the left.
  * Visit [Visitor Segments](https://help.optimizely.com/hc/en-us/articles/200040315-Visitor-Segments) for more on using Visitor Segments to analyze results.

#Optimizely Resources
* [Creating Experiments](https://help.optimizely.com/hc/en-us/articles/200136330-The-Five-Steps-In-Every-Test)
* [Targeting Experiments](https://help.optimizely.com/hc/en-us/sections/200008115-Targeting)
* [Segmentation](https://help.optimizely.com/hc/en-us/sections/200008125-Segmentation)
* [Optimizely Learning Center](https://help.optimizely.com/hc/en-us)
* [Optimizely 3rd Party Integrations](https://help.optimizely.com/hc/en-us/sections/200008075-3rd-Party-Integration)
* [Optimizely API Documentation](http://www.optimizely.com/docs/api)
