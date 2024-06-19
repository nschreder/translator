# Set up translator core components

This article helps you set up the core components of the Translator app. The core components are the foundation of the service, containing providing insights and customization option to tailor the solution based on your requirements.

## Before you start

### Create Azure services
The core component solution requires several Azure services which you must create first.
1. [Azure Storage account](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-create?tabs=azure-portal): This service is needed to temporarily store documents for the translation service.
2. [Azure Speech service](https://portal.azure.com/#create/Microsoft.CognitiveServicesSpeechServices): This service is needed to use the text to speech capabilities in the translation service.
3. [Azure Translator](https://learn.microsoft.com/en-us/azure/ai-services/translator/create-translator-resource). This service is needed to translate text and documents. **Important**: Only **'Global'** location subscription keys are supported.

### Create connections
We recomment that you create connections to all connectors used in the solution prior to importing the core component solution. This makes the setup faster.
1. Go to [Power Apps](https://make.powerapps.com/)
2. Select the environment you want to deploy the Translator solution
3. Go to **'Connections > + New connection'**.
4. Create connections for the following connectors using your credentials or a service account (if supported by connector):
    1. [Azure Blob Storage](https://learn.microsoft.com/en-us/connectors/azureblob/)
    2. [Azure Text to Speech](https://learn.microsoft.com/en-us/connectors/azuretexttospeech/)
    3. [Microsoft Dataverse](https://learn.microsoft.com/en-us/connectors/commondataserviceforapps/)
    4. [Microsoft Translator (V2)](https://learn.microsoft.com/en-us/connectors/translatorv2/)
    5. [Microsoft Translator (V3)](https://learn.microsoft.com/en-us/connectors/microsofttranslatorv/)
  
## Set up the Translator core components
1. Download the latest release of the [core components](/releases/tag/CoreComponents) solution to your computer.
2. Import the **'TranslatorCoreComponents_x_x_x_xx_managed.zip'** solution file. If you are not sure how to import a solution, you can check this [guide](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/import-update-export-solutions).
3. During solution import, you configure environment variable values. Make sure to have the following information ready:
    1. Document Expiration: Decimal number, the time in hours a document is valid and can be downloaded by the users. Example: **'72'**.
    2. Storage Account Base: Url (Text), the base url from your storage account. Example: **'https://[NAME_OF_YOUR_STORAGE_ACCOUNT].blob.core.windows.net'**.
4. After the solution import is successful, open the solution in the solution explorer and run the Power Automate flow **'Initial Setup'**. This flow connects to the Azure services and imports all necessary data.

## Customization
After the set up you are able to start with the [customization](customization.md) of the translation solution.
