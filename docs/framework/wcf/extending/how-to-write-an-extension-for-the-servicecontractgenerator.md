---
title: 'Como: escrever uma extensão para o ServiceContractGenerator'
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: b13b881a221ae0aa757b04c206125716a55f5b8c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795531"
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="dd7a9-102">Como: escrever uma extensão para o ServiceContractGenerator</span><span class="sxs-lookup"><span data-stu-id="dd7a9-102">How to: Write an Extension for the ServiceContractGenerator</span></span>
<span data-ttu-id="dd7a9-103">Este tópico descreve como gravar uma extensão para o <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span><span class="sxs-lookup"><span data-stu-id="dd7a9-103">This topic describes how to write an extension for the <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span></span> <span data-ttu-id="dd7a9-104">Isso pode ser feito implementando a <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interface em um comportamento de operação ou implementando a <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface em um comportamento de contrato.</span><span class="sxs-lookup"><span data-stu-id="dd7a9-104">This can be done by implementing the <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interface on an operation behavior or implementing the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span> <span data-ttu-id="dd7a9-105">Este tópico mostra como implementar a <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface em um comportamento de contrato.</span><span class="sxs-lookup"><span data-stu-id="dd7a9-105">This topic shows how to implement the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span>  
  
 <span data-ttu-id="dd7a9-106">O <xref:System.ServiceModel.Description.ServiceContractGenerator> gera contratos de serviço, tipos de cliente e configurações de <xref:System.ServiceModel.Description.ServiceEndpoint>cliente <xref:System.ServiceModel.Description.ContractDescription>de instâncias <xref:System.ServiceModel.Channels.Binding> , e.</span><span class="sxs-lookup"><span data-stu-id="dd7a9-106">The <xref:System.ServiceModel.Description.ServiceContractGenerator> generates service contracts, client types, and client configurations from <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances.</span></span> <span data-ttu-id="dd7a9-107">Normalmente, você importa <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>e <xref:System.ServiceModel.Channels.Binding> instâncias de metadados de serviço e, em seguida, usa essas instâncias para gerar código para chamar o serviço.</span><span class="sxs-lookup"><span data-stu-id="dd7a9-107">Typically, you import <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances from service metadata and then use these instances to generate code to call the service.</span></span> <span data-ttu-id="dd7a9-108">Neste exemplo, uma <xref:System.ServiceModel.Description.IWsdlImportExtension> implementação é usada para processar anotações WSDL e, em seguida, adicionar extensões de geração de código aos contratos importados para gerar comentários sobre o código gerado.</span><span class="sxs-lookup"><span data-stu-id="dd7a9-108">In this example, an <xref:System.ServiceModel.Description.IWsdlImportExtension> implementation is used to process WSDL annotations and then add code generation extensions to the imported contracts to generate comments on the generated code.</span></span>  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="dd7a9-109">Para gravar uma extensão para o ServiceContractGenerator</span><span class="sxs-lookup"><span data-stu-id="dd7a9-109">To write an extension for the ServiceContractGenerator</span></span>  
  
1. <span data-ttu-id="dd7a9-110">Implementar <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span><span class="sxs-lookup"><span data-stu-id="dd7a9-110">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="dd7a9-111">Para modificar o contrato de serviço gerado, use <xref:System.ServiceModel.Description.ServiceContractGenerationContext> a instância passada para <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> o método.</span><span class="sxs-lookup"><span data-stu-id="dd7a9-111">To modify the generated service contract, use the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instance passed into the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> method.</span></span>  
  
    ```  
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. <span data-ttu-id="dd7a9-112">Implemente <xref:System.ServiceModel.Description.IWsdlImportExtension> na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="dd7a9-112">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension> on the same class.</span></span> <span data-ttu-id="dd7a9-113">O <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> método pode processar uma extensão WSDL específica (neste caso, anotações WSDL) adicionando uma extensão de geração de código à instância importada <xref:System.ServiceModel.Description.ContractDescription> .</span><span class="sxs-lookup"><span data-stu-id="dd7a9-113">The <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method can process a specific WSDL extension (WSDL annotations in this case) by adding a code generation extension to the imported <xref:System.ServiceModel.Description.ContractDescription> instance.</span></span>  
  
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
  
3. <span data-ttu-id="dd7a9-114">Adicione o importador WSDL à sua configuração de cliente.</span><span class="sxs-lookup"><span data-stu-id="dd7a9-114">Add the WSDL importer to your client configuration.</span></span>  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. <span data-ttu-id="dd7a9-115">No código do cliente, crie uma `MetadataExchangeClient` chamada `GetMetadata`e.</span><span class="sxs-lookup"><span data-stu-id="dd7a9-115">In the client code, create a `MetadataExchangeClient` and call `GetMetadata`.</span></span>  
  
    ```  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. <span data-ttu-id="dd7a9-116">Crie uma `WsdlImporter` chamada `ImportAllContracts`e.</span><span class="sxs-lookup"><span data-stu-id="dd7a9-116">Create a `WsdlImporter` and call `ImportAllContracts`.</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. <span data-ttu-id="dd7a9-117">Criar um `ServiceContractGenerator` e chamar `GenerateServiceContractType` para cada contrato.</span><span class="sxs-lookup"><span data-stu-id="dd7a9-117">Create a `ServiceContractGenerator` and call `GenerateServiceContractType` for each contract.</span></span>  
  
    ```  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <span data-ttu-id="dd7a9-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>é chamado automaticamente para cada comportamento de contrato em um determinado contrato que <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>implementa.</span><span class="sxs-lookup"><span data-stu-id="dd7a9-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> is called automatically for each contract behavior on a given contract that implements <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="dd7a9-119">Esse método pode, então, <xref:System.ServiceModel.Description.ServiceContractGenerationContext> modificar o passado.</span><span class="sxs-lookup"><span data-stu-id="dd7a9-119">This method can then modify the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passed in.</span></span> <span data-ttu-id="dd7a9-120">Neste exemplo, comentários são adicionados.</span><span class="sxs-lookup"><span data-stu-id="dd7a9-120">In this example comments are added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd7a9-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd7a9-121">See also</span></span>

- [<span data-ttu-id="dd7a9-122">Metadados</span><span class="sxs-lookup"><span data-stu-id="dd7a9-122">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="dd7a9-123">Como: Importar WSDL personalizado</span><span class="sxs-lookup"><span data-stu-id="dd7a9-123">How to: Import Custom WSDL</span></span>](how-to-import-custom-wsdl.md)
