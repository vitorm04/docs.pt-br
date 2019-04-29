---
title: 'Como: escrever uma extensão para o ServiceContractGenerator'
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: c9e10efccf0d51e6b78aace1296d227a78a9f91d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766994"
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="89111-102">Como: escrever uma extensão para o ServiceContractGenerator</span><span class="sxs-lookup"><span data-stu-id="89111-102">How to: Write an Extension for the ServiceContractGenerator</span></span>
<span data-ttu-id="89111-103">Este tópico descreve como escrever uma extensão para o <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span><span class="sxs-lookup"><span data-stu-id="89111-103">This topic describes how to write an extension for the <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span></span> <span data-ttu-id="89111-104">Isso pode ser feito com a implementação de <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> um comportamento de operação de interface ou implementar o <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface em um comportamento de contrato.</span><span class="sxs-lookup"><span data-stu-id="89111-104">This can be done by implementing the <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interface on an operation behavior or implementing the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span> <span data-ttu-id="89111-105">Este tópico mostra como implementar o <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface em um comportamento de contrato.</span><span class="sxs-lookup"><span data-stu-id="89111-105">This topic shows how to implement the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span>  
  
 <span data-ttu-id="89111-106">O <xref:System.ServiceModel.Description.ServiceContractGenerator> gera os contratos de serviço, os tipos de cliente e as configurações de cliente do <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, e <xref:System.ServiceModel.Channels.Binding> instâncias.</span><span class="sxs-lookup"><span data-stu-id="89111-106">The <xref:System.ServiceModel.Description.ServiceContractGenerator> generates service contracts, client types, and client configurations from <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances.</span></span> <span data-ttu-id="89111-107">Normalmente, você importa <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, e <xref:System.ServiceModel.Channels.Binding> instâncias de metadados de serviço e, em seguida, use essas instâncias para gerar código para chamar o serviço.</span><span class="sxs-lookup"><span data-stu-id="89111-107">Typically, you import <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances from service metadata and then use these instances to generate code to call the service.</span></span> <span data-ttu-id="89111-108">Neste exemplo, um <xref:System.ServiceModel.Description.IWsdlImportExtension> implementação é usada para processar as anotações de WSDL e, em seguida, adicione as extensões de geração de código para os contratos importados para gerar comentários no código gerado.</span><span class="sxs-lookup"><span data-stu-id="89111-108">In this example, an <xref:System.ServiceModel.Description.IWsdlImportExtension> implementation is used to process WSDL annotations and then add code generation extensions to the imported contracts to generate comments on the generated code.</span></span>  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="89111-109">Para gravar uma extensão para o ServiceContractGenerator</span><span class="sxs-lookup"><span data-stu-id="89111-109">To write an extension for the ServiceContractGenerator</span></span>  
  
1. <span data-ttu-id="89111-110">Implementar <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span><span class="sxs-lookup"><span data-stu-id="89111-110">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="89111-111">Para modificar o contrato de serviço gerado, use o <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instância passada para o <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> método.</span><span class="sxs-lookup"><span data-stu-id="89111-111">To modify the generated service contract, use the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instance passed into the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> method.</span></span>  
  
    ```  
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. <span data-ttu-id="89111-112">Implemente <xref:System.ServiceModel.Description.IWsdlImportExtension> na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="89111-112">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension> on the same class.</span></span> <span data-ttu-id="89111-113">O <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> método pode processar uma extensão específica da WSDL (anotações WSDL neste caso), adicionando uma extensão de geração de código para o importados <xref:System.ServiceModel.Description.ContractDescription> instância.</span><span class="sxs-lookup"><span data-stu-id="89111-113">The <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method can process a specific WSDL extension (WSDL annotations in this case) by adding a code generation extension to the imported <xref:System.ServiceModel.Description.ContractDescription> instance.</span></span>  
  
    ```  
    public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)  
       {  
                // Contract documentation  
             if (context.WsdlPortType.Documentation != null)  
             {  
                    context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));  
             }  
             // Operation documentation  
             foreach (Operation operation in context.WsdlPortType.Operations)  
             {  
                if (operation.Documentation != null)  
                {  
                   OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);  
                   if (operationDescription != null)  
                   {  
                            operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));  
                   }  
                }  
             }  
          }  
          public void BeforeImport(ServiceDescriptionCollection wsdlDocuments, XmlSchemaSet xmlSchemas, ICollection<XmlElement> policy)   
            {  
                Console.WriteLine("BeforeImport called.");  
            }  
  
          public void ImportEndpoint(WsdlImporter importer, WsdlEndpointConversionContext context)   
            {  
                Console.WriteLine("ImportEndpoint called.");  
            }  
    ```  
  
3. <span data-ttu-id="89111-114">Adicione o importador WSDL para sua configuração de cliente.</span><span class="sxs-lookup"><span data-stu-id="89111-114">Add the WSDL importer to your client configuration.</span></span>  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. <span data-ttu-id="89111-115">No código do cliente, criar uma `MetadataExchangeClient` e chamar `GetMetadata`.</span><span class="sxs-lookup"><span data-stu-id="89111-115">In the client code, create a `MetadataExchangeClient` and call `GetMetadata`.</span></span>  
  
    ```  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. <span data-ttu-id="89111-116">Criar uma `WsdlImporter` e chamar `ImportAllContracts`.</span><span class="sxs-lookup"><span data-stu-id="89111-116">Create a `WsdlImporter` and call `ImportAllContracts`.</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. <span data-ttu-id="89111-117">Criar uma `ServiceContractGenerator` e chamar `GenerateServiceContractType` para cada contrato.</span><span class="sxs-lookup"><span data-stu-id="89111-117">Create a `ServiceContractGenerator` and call `GenerateServiceContractType` for each contract.</span></span>  
  
    ```  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <span data-ttu-id="89111-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> é chamado automaticamente para cada comportamento de contrato em um determinado contrato que implementa <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span><span class="sxs-lookup"><span data-stu-id="89111-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> is called automatically for each contract behavior on a given contract that implements <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="89111-119">Esse método pode modificar o <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passado.</span><span class="sxs-lookup"><span data-stu-id="89111-119">This method can then modify the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passed in.</span></span> <span data-ttu-id="89111-120">Neste exemplo, eles são acrescentados.</span><span class="sxs-lookup"><span data-stu-id="89111-120">In this example comments are added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89111-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89111-121">See also</span></span>

- [<span data-ttu-id="89111-122">Metadados</span><span class="sxs-lookup"><span data-stu-id="89111-122">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="89111-123">Como: Importar WSDL personalizado</span><span class="sxs-lookup"><span data-stu-id="89111-123">How to: Import Custom WSDL</span></span>](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
