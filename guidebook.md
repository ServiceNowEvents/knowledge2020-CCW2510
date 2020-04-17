
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

1. Click the **Action** button. Click the **London Transit** Spoke. Click the **List Line Statuses** Action.
    ![In the London Transit Spoke Select the List Line Statuses Action](images/027_select_list_line_statuses_action.png)
1. The Action is now part of the Flow.
    ![List Line Statuses Action is Now In Flow](images/028_list_line_statuses_action_on_flow.png)

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

# Define Action Inputs

Action Inputs allow you (and users of Flow Designer) to pass data into your actions. You can think of inputs as method parameters. This section will walk you through the process of creating Action Inputs for the **List Line Statuses** action.

## Input Naming Considerations

Action inputs should always have human-friendly names.

**GOOD**: First name

**BAD**: first\_name

**GOOD**: Table Name

**BAD**: tableName

## Add the Input

1. Click the **Inputs** section at the top of the **Action Outline**.
    ![Click the Input Header](images/034_select_inputs.png)
2. Click the **Create Input** button.
    ![Create Input](images/035_create_input_button.png)
3. Click the “variable” label and change the value to “Modes”. Leave the type as **String**. Turn the **Mandatory** toggle on.
    ![Alt Text](images/036_input_label.png)
4. Note that there is now a “Modes” pill in the **Input Variables** section of the Data pane.
    ![Modes Data Pill is now on screen](images/037_input_in_data_pane.png)
5. **Save** the Action.

## Change the Log step to use the input

Now that the action has an input, you will change the Log step to use the value from this input.

1. Open the step named **Log step**.
2. Add a space after the existing log message, and then *drag* the **Modes** input to the end of the **Log Message** input.
    ![Building Log Message with the Data Pill](images/038_build_log_message.png)
3. **Save** the action.
4. Click the **Test** button at the top of the Designer page.
 ![The Test Button for the Action](images/038a_test_button.png)
5. Fill in a value to the **Modes** field and click **Run Test**.
    ![Add Input to the Test](images/038b_test_action_form.png)
6. Follow the Execution Results link as before. Examine the results of the individual steps and verify that you see your input correctly logged.
    ![Results of the Test](images/039_test_results.png)

# The REST Step

In this exercise, we will use the REST step. The REST step is exclusive to IntegrationHub, and is only available after activating the IntegrationHub Installer plugin. This is already active in your lab instance.

## Add a REST Step to the Action

1. Click the + button underneath the Log step you added earlier.
    ![Add the REST Step](images/040_add_rest_step.png)
2. Click the REST step in the **Integrations** section of the dialog.
    ![Select the REST Step](images/041_select_rest_step.png)
3. You will be presented with the REST step UI.
    ![Define the REST Step](images/042_rest_step_ui.png)

### Define Connection Information

When configuring an REST step, there are two options for defining the endpoint you will connect to:

1. Use Connection Alias
2. Define Connection Inline

Whenever possible, you should use a Connection Alias when designing your step. There are two primary reasons to define connections inline:

1. Quick prototyping/testing.
2. When connection info is dynamic and will be passed into the action as an input or otherwise dynamically determined (e.g. the REST step will connect to an address defined in a Configuration Item record passed into the flow).

**Note**: Although the London Transport API needs no login, that is a rare case. In practice, almost every integration will require a Connection Alias.

In this exercise, we will start with an inline connection, and convert the action to use a Connection Alias later.

1. Change the **Connection** choice to “Define Connection Inline”.
. Set the **Base URL** to `https://api.tfl.gov.uk`
1. Set the **Resource Path** to `/Line/Mode/tube/Status`
1. Make sure there are no leading/trailing spaces in the Base URL and Resource Path fields.
1. Set the **HTTP Method** to “GET”.

### Add Headers

You will add one request header.

1. Beside the **Headers** widget, click the **+** icon.
    ![Alt Text](images/042b_add_header.png)

1. Set the header **Name** to `Content-Type`.
1. Set the header **Value** to `application/json`.
1. Again, make sure there is no extra whitespace at the beginning/end of these field values, and that the capitalization and dash in the header name are correct. HTTP is sensitive to all of this in headers.

The headers widget should now look something like this:

![Alt Text](images/043_headers.png)

**Save** the action.

### Test the Action

Using the same steps you followed earlier, test the action again. This time, inspect the details of the REST step. If everything worked correctly, you will see a response from the Transit API.

![Alt Text](images/044_result_of_rest_test.png)

## Data Pills

There’s problem with the REST step you just configured. You hard-coded the mode  ("tube") in the Resource Path. Action Designer gives you the ability to include “Data Pills” (those blue things in the Data Pane) in paths, in the body of POSTs and  even inside headers.

1. Inside the **Resource Path** backspace to remove the `tube` portion. Drag the **Modes** Data Pill from the input between the now empty slashes so that it looks like this:
    ![Drag the Data Pill to the Resource Path](images/042a_resource_path_with_pill.png)

1. Verify that there is no whitespace between the slashes and the data pill.

1. **Save** the action.

### Test the Action with the Data Pill in place

Test as you did before with the **Test** button. You will be presented with a form to enter the input of the action. Because this input is mandatory, you must provide some text. Try with "tube" to verify you see the same text as before. Then for fun, try with "river-bus" or "cable-car" (or even both, comma separated.) Try as well with nonsense text to see the result of that input.

# Configure a Connection Alias and Connection

There’s another problem with the action you just built. You hard-coded the connection information into the action. If you were talking to a development system and then moved the action into a production environment, or any authentication changes you would have to modify the action directly.

**Connection Aliases** allow you to decouple connection information from the actions you design. They give you the flexibility to build and distribute actions without knowing the connection info beforehand. This gives admins the ability to configure/maintain connections without having to touch the action itself.

## Create a Connection Alias

In this section, you will create a Connection Alias to be used by all of the actions in your spoke.

1. Make sure the correct application is active.
    ![Alt Text](images/048_verify_active_application.png)
2. Navigate to **Connections & Credentials \> Connection & Credential Aliases**.
3. Click **New**.

    ![Alt Text](images/049_new_connection_alias.png)

4. Set the following fields:
    - **Name**: CC20_London_Transit
    - **Type**: Connection & Credential
    - **Connection type**: HTTP
    ![Alt Text](images/050_connection_alias_form.png)
5. Right click the header and click the **Save** button to save the Connection Alias.

    ![Alt Text](images/051_right_click_save_alias.png)

### Connection Attributes

In addition to the core properties that can be defined in a connection (e.g. endpoint, port, etc.), you can define additional **Connection Attributes** that will be made available to the Actions using that connection alias.

### Define a Connection Attribute

1. Make sure the Connection Alias you just created is open.
2. Select the **Connection Attributes** tab and click the **New** button.

    ![Alt Text](images/052_new_attribute.png)

3. Set the following field values:

    **Type:** String

    **Label:** Version

    **Column name:** \<leave the generated value\>

    **Max length:** 10

    ![Alt Text](images/053_new_attribute_form.png)
4. Click the **Submit** button.

## Create a Connection

By itself, an Alias doesn’t do anything. You must define a **Connection** in order to actually use the Alias. In this lab, you will only create a single connection, but imagine a scenario where you have separate connections for a dev, test, and production environment.

The API in this lab does not require  authentication for most endpoints although it does have some. When using an API with API keys, passwords or OAuth configuration it would be configured as a Credential associated with this Connection. Understand that for future use that this is the correct spot, although not required now.

1. From the Connection Alias form, switch to the **Connections** tab. Click the **New** button.

    ![Alt Text](images/054_new_connection.png)

1. Set the **Name** to “London Transit (Lab)”.
1. Set the **Connection URL** to

    `https://api.tfl.gov.uk`

1. Under the **Attributes** section, set the **Version** to the "1".
1. The form should look something like this:

    ![Alt Text](images/055_new_connection_form.png)

1. Click the **Submit** button to create the connection.

### Update the REST Step to Use the Alias

You must now update the REST step to use the connection Alias and the Subscription Key attribute instead of the hard coded values.

1. Open the REST Step in the Action you created earlier.
1. Change the **Connection** field to “Use Connection Alias”.
1. Set the **Connection Alias** field to the Alias you just created.

    ![Alt Text](images/056_connection_details.png)
1. **Save** the action.
1. **Test** the action again, and make sure everything still works.

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
1. Set the **Label** and **Name** to “statuses”.
1. Set the **Type** to “Array.Object”.
1. Set the **Label** and **Name** of the child object to "status".
1. We need the structure of the objects to mirror the JSON objects created above in script. Create three fields on the "status" object by clicking the **+** button icon.
    ![Alt Text](images/059a_create_complex_object.png)
1. Use the **Label** and **Name** as "name", "description", and "reason". Leave the Type as **String** for all three.
    ![Alt Text](images/059b_final_complex_object.png)
1. You will now see a new data pill in the **Script step** section of the Data Pane.

# Action Outputs

Use Action Outputs to return data from the action to Flow Designer. The Script Output Variable we just defined is intentionally “private” to the action and is intended for use by scripts or other action steps (thus, the camel case naming convention).

The same naming considerations we used for Action Inputs also apply to Action Outputs. Outputs should always be human readable, use natural language, and should not contain underscores or use variable naming conventions like camelCase.

**GOOD**: Score.
**BAD**: score.

1. Click the **Outputs** section in the **Action Outline**.
1. Click the **+ Create Output** button.
1. Set the **Label** to “Statuses”. Do not fill out the complex object. Click the **Exit Edit Mode** button.

    ![Alt Text](images/060a_create_action_output.png)
1. Using the Data Pill Picker, set the **Value** to the statuses Script Output Variable.

    ![Alt Text](images/061_outputs.png)
1. Click the **Edit Outputs** button again to verify the complex object output was automatically created.
    ![Alt Text](images/061a_create_complex_object_output.png)

1. **Save** the Action.

## Use the Output

Now that the action is returning the score, you can use it in the Flow. Make the following modifications to the test flow you created.

1. Change the **Modes** input on the List Line Statuses action to use the text "tube".
1. Add a **Log** step. For the **Message** use the Statuses data pill that was created for the List Line Statuses action.

At this point, your flow should look something like this.

![Alt Text](images/062_updated_flow_up_to_now.png)

## Publish the Action

Run a test of the flow. Look at the Execution Plan and verify you see a JSON object of bus and tube statuses in the Log statement.

If everything looks good, click the **Publish** button on the action to make it available for all flows.

# Create a REST Integration from OpenAPI

In the previous exercises, you created your endpoints by entering all of the data yourself. For APIs that publish an OpenAPI specification, you can automatically import all the information about all endpoints in the API. In this exercise, you will integrate to a new endpoint in the London Transport API quickly via OpenAPI import and the XML Parser step.

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

Congratulations! You have created a full integration via OpenAPI and created an Action that integrates to it.
  