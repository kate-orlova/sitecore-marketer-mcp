# Create a new datasource item

## Prompt
To create a new datasource item for a specific component, use the following prompt. Replace the component name and field values as required:
```
Create a Promo datasource for Home with Text "Black Friday"
```

## Output
Here is a response from Claude after creating the datasource item:
![Create Component Datasource](../../assets/prompts/create_component_ds-1.png)

While Claude processes your request it may ask for permission to use the `List Components` and `Get Component` tools to retrieve information about the requested component including its ID and datasource configuration. You will see the following notifications:

![Permission to use List Components](../../assets/prompts/create_component_ds-2.png)
![Permission to use Get Component](../../assets/prompts/create_component_ds-3.png)

After validating that the requested component exists and retrieving its datasource configuration, Claude will proceed with creating the datasource item using the provided field values. It will then ask for permission to use the `Create Component Datasource` tool:

![Permission to use Create Component Datasource](../../assets/prompts/create_component_ds-4.png)




