# Set up translator core components

This article helps you set up the core components of the Translator app. The core components are the foundation of the service, providing insights and offering customization options to tailor the solution based on your requirements.

## Before you start

### Create Azure services
The core component solution requires several Azure services which you must create first.
1. [Azure Storage account](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-create?tabs=azure-portal): This service is needed to temporarily store documents for the translation service. **Important**: If your storage account is behind a firewall, you must enable [additional configurations](https://learn.microsoft.com/en-us/azure/ai-services/translator/connector/document-translation-flow?tabs=blob-storage#azure-storage).
2. [Azure Speech service](https://portal.azure.com/#create/Microsoft.CognitiveServicesSpeechServices): This service is needed to use the text to speech capabilities in the translation service.
3. [Azure Translator](https://learn.microsoft.com/en-us/azure/ai-services/translator/create-translator-resource) for text translation: This service is needed to translate text. **Important**: Only **'Global'** location subscription keys and **'single-service Translator resources'** are supported.
4. [Azure Translator](https://learn.microsoft.com/en-us/azure/ai-services/translator/create-translator-resource) for document translation: This service is needed to translate documents. **Important**: Do not use the **'Global'** location and only **'single-service Translator resources'** are supported.

### Create connections
We recommend that you create connections to all connectors used in the solution prior to importing the core component solution. This makes the setup process faster.
1. Go to [Power Apps](https://make.powerapps.com/).
2. Select the environment you want to deploy the Translator solution.
3. Go to **'Connections > + New connection'**.
4. Create connections for the following connectors using your credentials or a service account (if supported by connector):
    1. [Azure Blob Storage](https://learn.microsoft.com/en-us/connectors/azureblob/): Connect with your Azure Storage account service.
    2. [Azure Text to Speech](https://learn.microsoft.com/en-us/connectors/azuretexttospeech/): Connect with your Azure Speech service.
    3. [Microsoft Dataverse](https://learn.microsoft.com/en-us/connectors/commondataserviceforapps/): Connect with your personal or service principal credentials.
    4. [Microsoft Translator (V2)](https://learn.microsoft.com/en-us/connectors/translatorv2/): Connect with your Azure Translator service for text service.
    5. [Microsoft Translator (V3)](https://learn.microsoft.com/en-us/connectors/microsofttranslatorv/): Connect with your Azure Translator service for document services.
  
## Set up the Translator core components
1. Download the latest release of the [core components](https://github.com/nschreder/translator/releases/tag/CoreComponents) solution to your computer.
2. Import the **'TranslatorCoreComponents_x_x_x_xx_managed.zip'** solution file. If you are not sure how to import a solution, you can check this [guide](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/import-update-export-solutions).
3. During solution import, you configure connection references. Make sure to have the following information ready:
    1. Azure Blob Storage
    2. Azure Text to Speech
    3. Microsoft Dataverse
    4. Microsoft Translator (Documents)
    4. Microsoft Translator (Text)
4. In the next step, you configure environment variable values:
    1. **Document Expiration**: Decimal number, the time in hours a document is valid and can be downloaded by the users. Example: **'72'**.
    2. **Storage Account Base**: Url (Text), the base url from your storage account. Example: **'https://[NAME_OF_YOUR_STORAGE_ACCOUNT].blob.core.windows.net'**.
5. After the solution import is successful, open the solution in the solution explorer and run the Power Automate flow **'Initial Setup'**. This flow connects to the Azure services and imports all necessary data.

## Customization
After the setup, you are able to start with the [customization](/TranslatorManagement/customization.md) of the translation solution.
