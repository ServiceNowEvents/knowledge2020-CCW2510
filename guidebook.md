
# Lab Overview

IntegrationHub gives developers, admins and business process owners a centralized place to build and manage integrations. “Content” in IntegrationHub is made up of a series of “Spokes”. Spokes are self-contained scoped applications that contain all of the artifacts that make up an integration, primarily “Actions”.

This lab guide will walk you through the process of creating your first Spoke and will focus on the most common tasks required to build a Spoke from start to finish.

# Create a Scoped Application

Spokes are just Scoped Applications. It’s really that simple. Also, try saying “A Spoke is a Scope” ten times fast ...

The first task when building a new Spoke is to create a Scoped Application.

## Naming your Spoke

When choosing a name for your Spoke, you should keep a few things in mind.

1. The name you give the Spoke (application) will show up in the Action explorer in Flow Designer.
1. To make it easier to distinguish Spoke apps from other apps, add “Spoke” to the end of the application name. When the Spoke is rendered in the Flow Designer UI, the word “Spoke” will be removed.

    **Application Record**:
    ![Create Application](images/001_create_application.png)

    **Flow Designer UI**:
    ![Add the Action to a Flow](images/002_flow_designer_new_spoke.png)

## Create the Spoke

1. Navigate to **System Applications \> Studio**.

    ![Navigate to Studio](images/003_nav_to_studio.png)

1. Click the **Create Application** button.
1. Fill out the “Create Application” form with the following values:

    **Name**: London Transit Spoke

    **Scope**: [will be autofilled]
    ![Create New App Form](images/005_new_app_form.png)
1. Click the **Create** button.
1. In the subsequent dialog click the **Continue in Studio (Advanced)** link.
    ![Continue in Studio](images/005a_continue_in_studio.png)
1. Click the **London Transit Spoke** entry to open the new application in Studio.
    ![Alt Text](images/006_pick_application.png)

## Set the Spoke Icon

When building a Spoke, you can set an icon associated with the application. This will be rendered in the Flow Designer UI. For this lab exercise, you are responsible for finding the image of your choosing.

1. Using Google Images or a similar service, find the icon you wish to use.
2. In Studio, click **File \> Settings**.
    ![File Settings](images/007_file_settings.png)
3. Click the **Click to add…** link next to the Logo field.
    ![Click to Add Logo](images/008_click_to_add_logo.png)
4. Click the **Browse…** button and navigate to the image you chose.
    ![Browse to the Image You Downloaded](images/009_browse_choose_image_file.png)
5. Click the **OK** button. The image you chose will now be shown.
    ![Click OK](images/010_image_has_been_chosen.png)

# Create your first Action

Now that you have a scoped app to work with, it’s time to create your first Action. All of the actions you create in this lab will be created **in** the Scope you created.

## Launch Flow Designer

To launch Flow Designer, navigate to **Flow Designer > Designer**.

![Flow Designer User Interface](images/011_launch_flow_designer.png)

This opens a new UI where you will manage and build Actions, Flows and Subflows.

![Alt Text](images/012_flow_designer_ui.png)

## Create the First Action

1. Click the **+ New** button, and then click **Action** in the resulting menu.

    ![Click Action](images/013_new_action.png)

2. Fill out the Action Properties form.

    **Name:** List Valid Modes

    **Application:** London Transit Spoke

    **Description:** Enter a description - simple HTML tags are also supported

    ![Alt Text](images/014_action_description.png)

3. Click the **Submit** button and you will be taken to the new/empty Action.

    ![Alt Text](images/015_new_empty_action.png)

## Add a Log step

Actions are made up of a series of steps. You will now add a simple Log step to the action for testing purposes. We’ll add real integration logic to this Action in upcoming exercises.

1. Click the **Add a new step** button (+).
    ![Alt Text](images/016_add_new_step.png)
2. A new dialog will open with a list of available action steps. Click the **Log** step to add it to the Action.
    ![Select the Log Step](images/017_select_log_step.png)
3. Leave the **Log Level** at "Info" and set the **Log Message** field to "Hello, World!".
    ![Add the Log Step](images/018_log_step_hello_world.png)
4. Click the **Save** button on the Action. **Do not** click the Publish button yet. We’ll get to that in a bit.

# Create a Test Flow

Now that you have an Action, you need a Flow to test it.

1. Click the **+ New** button, and then click **Flow** in the resulting menu.
    ![Alt Text](images/019_create_new_flow.png)
2. Name the Flow “Test Flow” and click the **Submit** button.
    ![Alt Text](images/020_new_flow_form.png)

## Add a Trigger

Flows run when a Trigger condition is met. For this test, we will run a flow on a scheduled basis.

1. Click the **Select to add a trigger** button.
    ![Select to Add a Trigger](images/021_select_to_add_trigger.png)
2. Under the **Date** section, click **Daily**.
    ![Select Daily Trigger](images/022_select_daily_trigger.png)
3. Set to any time and click **Done**.
    ![Select Daily Trigger](images/023_configure_trigger.png)

### Enable Draft Actions

By default, only **Published** actions will show up in Flow Designer. Remember when we **didn’t** press the Publish button on the Action? When testing unpublished Actions, you must first enable the option to show draft actions.

1. Click the **More Actions** button (aka the "kebab menu") and click **Configurations**.
    ![Select Configurations](images/024_select_more_actions_configurations.png)
2. Turn on the **Show draft actions** toggle.
    ![Alt Text](images/025_click_show_draft_actions.png)
3. Close the **Configurations** dialog.

### Add the Action to the Flow

Now it’s time to add your action to the test flow.

1. Click the **Select to add an Action, Flow Logic, or Subflow** link.

    ![Select to add Action](images/026_select_to_add_action.png)

2. Click the **Action** button.
3. Click the **London Transit** Spoke.
4. Click the **List Valid Modes** Action.
    ![In the London Transit Spoke Select the List Valid Modes Action](images/027_select_list_valid_modes_action.png)
5. The Action is now part of the Flow.
    ![List Valid Modes Action is Now In Flow](images/028_list_valid_modes_action_on_flow.png)

### Test the Flow

1. To test the flow, click the **Test** button.
    ![Click the Test buttom](images/029_click_test_button.png)
2. A Dialog will open. Click the **Run Test** button.
    ![Click Run Test](images/030_configure_test.png)
3. Click the **Flow has been executed. To view the flow, click here** link.
    ![Click the View Flow Li](images/031_flow_has_been_exec_link.png)
4. This will open the Execution Details for the test run.
    ![Open Execution Details](images/032_execution_details.png)
5. Click the **List Valid Modes** action to expand details about the execution of that action. Click the **Logs** and **Steps** section to expand them. Note that the Logs section will show all logs generated by the action. The Steps section will show the list of steps executed inside of the action, and the step configuration details such as design time and run time values.
    ![Execution Details Expanded](images/033_execution_details_expanded.png)

# Create a REST Integration

In this exercise, you will integrate to the London Transport API quickly via OpenAPI import and the XML Parser step.

## Import Endpoints via OpenAPI

When integrating to external systems with IntegrationHub, OpenAPI can be a great convenience. This allows for the automatic import of all the endpoints defined in the OpenAPI specification. Not only is this a great timesaver but it increases the quality and efficiency of the integration by guaranteeing correctness of the input and output parameters.

1. Navigate to the tab for the **List Valid Modes** action or reopen if it has been closed.
1. Add a new step above the Log step by clicking the **+** icon above it.
1. Under the **Integrations** section select the **REST** step
 ![Execution Details Expanded](images/032b_add_rest_step.png)
1. Under the **Request Details** section change the **Build Request** option from **Manually** to **From OpenAPI Specification**. The **Import OpenAPI** button is now visible. Click it.
   ![Click Import OpenAPI](images/032c_import_openapi.png)
  
1. In the **Import OpenAPI Specification** dialog, ensure that **Import Method** is set to **Manually Populate OpenAPI Content**. Open the [OpenAPI specifiation file](files/london-transport.yaml) in a text editor. Copy the contents and paste into the field **OpenAPI Content**. Click **Import**.
   ![Complete OpenAPI dialog](images/032d_import_openapi_dialog.png)
1. In the **API Operation** field, type in "*mode" to search on the possible choices that contain that text. Select "Get a list of valid modes" choice.
1. Examine the populated values after the selection is made. The **Resource Path**, **HTTP Method** and **Headers** are automatically filled in.

## Define the REST Integration

With the REST step created, now you will configure the parsing of the return value.

1. Under the REST Step, delete all of the **Accept** header entries except for **text/xml** by clicking the trash can icons to the right.
1. Click the existing **Log** step. Delete the value in the **Log Message** field. From the right side, drag the Data Pill named **Response Body** and drop it in the **Log Message** field.
   ![Add Response Body to Log Message](images/032f_configure_log_message.png)
1. Click the **Test**  button. Click the link to open the execution details. Expand the **Steps** section and scroll to the bottom.
   ![Find the Results of the Log Step](images/032g_log_results.png)
1. Click the XML text on the right under **Runtime Values**. This will open a dialog viewer that shows the full response body. Select it and either keep on your clipboard or paste somewhere for safe keeping.
   ![Open ](images/032h_xml_payload.png)
1. Add a step below the **Log** step by click the **+* icon below it. Choose the **XML Parser** step.
   ![Add XML Parser Step](images/032i_add_xml_parser_step.png)
1. Paste the XML into the field under **Payload View** then click **Generate Target**.
   ![Generate Target](images/032j_generate_target.png)
1. You will now see the structure of the pasted XML payload represented as a complex object. Drag the Data Pill for **Response Body** and drop it into **Source Data** field on the left.
   ![Generated Target Configured for Data](images/032k_generated_target.png)

## Connect to Action Output

Now that the REST Step and XML Parser are configured you will finalize this action by connecting those steps to the action outputs.

1. Click the **Output** section on the left. Click the **Create Output** link.
   ![Create Output for the Action](images/032l_create_output.png)
1. There will be a default variable created. Overwrite that with these values:

    **Label**: Modes

    **Name**: modes

    **Type**: Array:Object

    ![Configure Variable](images/032m_configure_variable.png)
1. Although you could define the structure of the payload manually, there is a shortcut. Do not edit the child Object. Click **Exit Edit Mode**. Drag the **array_of_mode** Data Pill from the XML Parser section on the right to the **Value** field. DO NOT drag the top-most object, but instead the Array.object child under that.
    ![Drag Array.Object to Value](images/032n_drag_array_of_objects.png)
1. Click the **Edit Outputs** button again. Examine the structure automatically created after dropping the data pill.
    ![Automatically Created Structure](images/032o_created_structure.png)
1. Perform a final test of this Action by clicking the **Test** button and looking at the **Execution Details**. Click the payload underneath the **Runtime Value** section to open the viewer.
    ![Results of Final Test](images/032p_final_test.png)
1. Look at the results in the viewer. You should see a parsed version of the XML payload that looks similar to the below.
    ![Results of Final Test](images/032q_final_output.png)

Congratulations! You have created a full integration via OpenAPI and created your first Action that integrates to it.
  
# Define Action Inputs

Action Inputs allow you (and users of Flow Designer) to pass data into your actions. You can think of inputs as method parameters. This section will walk you through the process of creating Action Inputs for the **Get Sentiment Score** action.

## Input Naming Considerations

Action inputs should always have human-friendly names.

**GOOD**: First name
**BAD**: first\_name

**GOOD**: Table Name
**BAD**: tableName

## Add the Input

1. Click the **Inputs** section at the top of the **Action Outline**.
    ![Alt Text](images/034_select_inputs.png)
2. Click the **Create Input** button.
    ![Alt Text](images/035_create_input_button.png)
3. Click the “variable” label and change the value to “Text”. Turn the **Mandatory** toggle on.
    ![Alt Text](images/036_input_label.png)
4. Note that there is now a “Text” pill in the **Input Variables** section of the Data pane.
    ![Alt Text](images/037_input_in_data_pane.png)
5. **Save** the Action.

## Change the Log step to use the input

Now that the action has an input, you will change the Log step to use the value from this input.

1. Open the step named **Log step**.
2. Add a space after the existing log message, and then *drag* the **Text** input to the end of the **Log Message** input.
    ![Alt Text](images/038_build_log_message.png)
3. **Save** the action.
4. Open the **Test Flow** flow you created earlier.
5. Expand the **Get Sentiment** action and add a value to the new Text input.
    ![Alt Text](images/039_set_get_sentiment_inputs.png)
6. Test the flow again using the steps described earlier, and you will now see the “Text” value in the log message.

# The REST Step

In this exercise, we will use the REST step. The REST step is exclusive to IntegrationHub, and is only available after activating the IntegrationHub Installer plugin. This is already active in your lab instance.

## Add a REST Step to the Action

1. Click the + button underneath the Log step you added earlier.
    ![Alt Text](images/040_add_rest_step.png)
2. Click the REST step in the **Integrations** section of the dialog.
    ![Alt Text](images/041_select_rest_step.png)
3. You will be presented with the REST step UI.
    ![Alt Text](images/042_rest_step_ui.png)

### Define Connection Information

When configuring an REST step, there are two options for defining the endpoint you will connect to:

1. Use Connection Alias
2. Define Connection Inline

Whenever possible, you should use a Connection Alias when designing your step. There are two primary reasons to define connections inline:

1. Quick prototyping/testing.
2. When connection info is dynamic and will be passed into the action as an input or otherwise dynamically determined (e.g. the REST step will connect to an address defined in a Configuration Item record passed into the flow).

In this lab, we will start with an inline connection, and convert the action to use a Connection Alias later.

1. Change the **Connection** choice to “Define Connection Inline”.
. Set the **Base URL** to `https://westcentralus.api.cognitive.microsoft.com`
1. Set the **Resource Path** to `/text/analytics/v2.0/sentiment`
1. Make sure there are no leading/trailing spaces in the Base URL an Resource Path fields.
1. Set the **HTTP Method** to “POST”.

### Add Headers

You will add two request headers.

1. Inside the **Headers** widget, click the **+ Add** button.
2. Set the header **Name** to `Content-Type`.
3. Set the header **Value** to `application/json`.
4. Add another header.
5. Set the header **Name** to `Ocp-Apim-Subscription-Key`.
6. Set the header **Value** to the Subscription Key you saved from Microsoft earlier.
7. Again, make sure there is no extra whitespace at the beginning/end of these field values.

The headers widget should now look something like this:

![Alt Text](images/043_headers.png)

### Set Request Body

Under the **Request Content** section, set the **Request Body** to:

    {
       "documents":  [
            {
                "language": "en",
                "id": "string",
                "text": "I <3 IntegrationHub"
            }
        ]
    }

**Save** the action.

### Test the Action

Using the same steps you followed earlier, test the action again. This time, inspect the details of the REST step. If everything worked correctly, you will see a response from the Sentiment API.

![Alt Text](images/044_result_of_rest_test.png)

## Data Pills

There’s problem with the REST step you just configured. You hard-coded the message into the Body. Action Designer gives you the ability to include “Data Pills” (those blue things in the Data Pane) inside the Payload.

1. Remove the hard coded message from the “text” property in the payload.
2. With the cursor inside the quotes, click the Data Pill Picker.
    ![Alt Text](images/045_data_pill_picker.png)
3. Click **Inputs** and then click the **Text** input you created earlier.
    ![Alt Text](images/046_data_pill_picker_select_text_input.png)
4. You should now see the **action -\> Text** data pill inside the “text” property of the payload. If there are any extra spaces between the data pill and the closing quote, remove them.
    ![Alt Text](images/047_request_body_with_pill.png)
5. **Save** the action.

### Test the Action with the Data Pill in place

Go back to your test flow, and set the input of the flow to the sentence you would like to analyze. Test the flow, and make sure the Action input made it into the Sentiment API call.

# Configure a Connection Alias and Connection

There’s another problem with the action you just built. You hard-coded the connection information into the action, including the Subscription Key. If you were talking to a development system and then moved the action into a production environment, or the subscription key changes, you’d have to modify the action directly, which is definitely not something you should do.

**Connection Aliases** allow you to decouple connection information from the actions you design. They give you the flexibility to build and distribute actions without knowing the connection info beforehand. This gives admins the ability to configure/maintain connections without having to touch the action itself.

## Create a Connection Alias

In this section, you will create a Connection Alias to be used by all of the actions in your spoke.

1. Make sure the correct application is active.
    ![Alt Text](images/048_verify_active_application.png)
2. Navigate to **Connections & Credentials \> Connection & Credential Aliases**.
3. Click **New**.

    ![Alt Text](images/049_new_connection_alias.png)

4. Set the following fields:
    - **Name**: CC18\_MS\_Text\_Analytics
    - **Type**: Connection & Credential
    - **Connection type**: HTTP
    ![Alt Text](images/050_connection_alias_form.png)
5. Right click the header and click the **Save** button to save the Connection Alias.

    ![Alt Text](images/051_right_click_save_alias.png)

### Connection Attributes

In addition to the core properties that can be defined in a connection (e.g. endpoint, port, etc.), you can define additional **Connection Attributes** that will be made available to the Actions using that connection alias.

### Define a Connection Attribute

The API we are communicating with requires us to send a **Subscription Key** with every request. This will not be sent as part of a traditional Basic Auth or OAuth credential, so we will use a Connection Attribute to store and access this value.

1. Make sure the Connection Alias you just created is open.
2. Select the **Connection Attributes** tab and click the **New** button.

    ![Alt Text](images/052_new_attribute.png)

3. Set the following field values:

    **Type:** String
    **Label:** Subscription Key
    **Column name:** \<leave the generated value\>
    **Max length:** 100

    ![Alt Text](images/053_new_attribute_form.png)
4. Click the **Submit** button.

## Create a Connection

By itself, an Alias doesn’t do anything. You must define a **Connection** in order to actually use the Alias. In this lab, you will only create a single connection, but imagine a scenario where you have separate connections for a dev, test, and production environment.

1. From the Connection Alias form, switch to the **Connections** tab. Click the **New** button.

    ![Alt Text](images/054_new_connection.png)

2. Set the **Name** to “MS Text Analytics (West)”.
3. Set the **Connection URL** to

    `https://westcentralus.api.cognitive.microsoft.com`

4. Under the **Attributes** section, set the **Subscription Key** to the key you obtained earlier in this lab.
5. The form should look something like this:

    ![Alt Text](images/055_new_connection_form.png)

6. Click the **Submit** button to create the connection.

### Update the REST Step to Use the Alias

You must now update the REST step to use the connection Alias and the Subscription Key attribute instead of the hard coded values.

1. Open the REST Step in the Action you created earlier.
2. Change the **Connection** field to “Use Connection Alias”.
3. Set the **Connection Alias** field to the Alias you just created.

    ![Alt Text](images/056_connection_details.png)

4. Notice that a new variable called **Subscription Key** is now available in the Data Pane section for the REST Step.

    ![Alt Text](images/057_data_pane_subscription_key.png)

5. Remove the hard-coded Subscription Key from the `Ocp-Apim-Subscription-Key` header.
6. Drag the **Subscription Key** data pill from the data pane to the value field.

    ![Alt Text](images/058_drag_subscription_key_to_header.png)

7. **Save** the action.
8. **Test** the action again, and make sure everything still works.

The Action is now fully reusable! You can now pass data into the action, and configure connection / subscription key information without modifying the action.

# The Script Step

Right now, the Action is getting a sentiment score, but isn’t doing anything useful with it. In this exercise, you will use a Script Step to parse the output of the REST step.

Script Steps give you access to the full power of the ServiceNow platform. You can make calls to any server-side scripts (as long as they are available in your scope) and they give you the power to create new kinds of actions that don’t yet exist.

1. Add a new Action Step after the REST step. When prompted, choose the **Script** step.

    ![Alt Text](images/059_script_step_button.png)

## Script Input Variables

The script step gets its own set of input variables. This allows you to map data from the data pane into script-friendly variables.

1. In the **Input Variables** widget, click the **+ Create Variable** button.
2. Set the **Name** to `responseBody`.
3. Drag the **Response Body** data pill from the data pane to the **Value** field. You can now reference the Response Body in your script as `inputs.responseBody`.

    ![Alt Text](images/060_response_body_script_input.png)

4. Set the script to:

```javascript
(function execute(inputs, outputs) {
    var scoreObject = JSON.parse(inputs.responseBody);
    var score = Number(scoreObject.documents[0].score);
    outputs.score = score.toFixed(2);
})(inputs, outputs);
```

## Script Output Variables

You may notice that the script is setting something you haven’t yet defined: `outputs.score`.

Similar to Script Input Variables, Script Output Variables allow you to pass data out of your script to other steps in the action. These variables are internal to the action, and are not surfaced in Flow Designer.

1. In the **Output Variables** widget, click the **+ Create Variable** button.
2. Set the **Name** to “score”.
3. Set the **Type** to “Floating Point Number”.
4. You will now see a new data pill in the **Script step** section of the Data Pane.

# Action Outputs

Use Action Outputs to return data from the action to Flow Designer. The Script Output Variable we just defined is intentionally “private” to the action and is intended for use by scripts or other action steps (thus, the camel case naming convention).

The same naming considerations we used for Action Inputs also apply to Action Outputs. Outputs should always be human readable, use natural language, and should not contain underscores or use variable naming conventions like camelCase.

**GOOD**: Score.
**BAD**: score.

1. Click the **Outputs** section in the **Action Outline**.
2. Click the **+ Create Output** button.
3. Set the **Label** to “Score”.
4. Using the Data Pill Picker, set the **Value** to the “score” Script Output Variable.

    ![Alt Text](images/061_outputs.png)

5. **Save** the Action.

## Use the Output

Now that the action is returning the score, you can use it in the Flow. Make the following modifications to the test flow you created.

1. Change the **Text** input on the Get Sentiment Score action to use the **Trigger -\> Incident Record -\> Short description** data pill.
2. Add an **Add Worknote** action to the flow.
3. Set the **Task [Incident]** to the **Trigger -\> Incident Record** data pill.
4. Set the **Work note** to “Sentiment score for incident is: (1 -\> Score)”, where “(1 -\> Score)” is the Score output from the Get Sentiment Score action.

At this point, your flow should look something like this.

![Alt Text](images/062_updated_flow_up_to_now.png)

## Publish the Action

Run another test, and go check the Incident record to see the work note added by the flow.

If everything looks good, click the **Publish** button on the action to make it available for all flows.

# Challenge Exercise

If you have completed the other exercises early and wish to continue learning, consider implementing a solution to the following use case building on the work you have done thus far.

## Use case

A new team has been formed to handle customer issues. The team is called "Customer Success" and consists of the following team members:

- Abraham Lincoln
- John Adams
- George Washington

Your job is to create a "customer response" record based on sentiment scores below 0.20 and assign it to the customer success team.

Here's a rough outline of things you'll need to do:

1. Create a new customer success group with the members listed above.
1. Create a new customer response table.
1. Use the action you created in your custom spoke to identify records with a given score.
1. Based on that score, create a record in the customer response table.
