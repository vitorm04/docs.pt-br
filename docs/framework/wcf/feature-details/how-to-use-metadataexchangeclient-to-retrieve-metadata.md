---
title: 'Como: usar MetadataExchangeClient para recuperar metadados'
ms.date: 03/30/2017
ms.assetid: 0754e9dc-13c5-45c2-81b5-f3da466e5a87
ms.openlocfilehash: c9558e1943c3886a61c3b19801e22d57732e459a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968759"
---
# <a name="how-to-use-metadataexchangeclient-to-retrieve-metadata"></a>Como: usar MetadataExchangeClient para recuperar metadados
Use a <xref:System.ServiceModel.Description.MetadataExchangeClient> classe para baixar metadados usando o protocolo WS-MetadataExchange (MEX). Os arquivos de metadados recuperados são retornados <xref:System.ServiceModel.Description.MetadataSet> como um objeto. O objeto <xref:System.ServiceModel.Description.MetadataSet> retornado contém uma coleção de <xref:System.ServiceModel.Description.MetadataSection> objetos, cada um contendo um dialeto de metadados específico e um identificador. Você pode gravar os metadados retornados em arquivos ou, se os metadados retornados contiverem documentos WSDL (Web Services Description Language), você poderá importar os metadados <xref:System.ServiceModel.Description.WsdlImporter>usando o.  
  
 Os <xref:System.ServiceModel.Description.MetadataExchangeClient> construtores que assumem um endereço usam a associação <xref:System.ServiceModel.Description.MetadataExchangeBindings> na classe estática que corresponde ao esquema de Uniform Resource Identifier (URI) do endereço. Como alternativa, você pode usar <xref:System.ServiceModel.Description.MetadataExchangeClient> o construtor que permite especificar explicitamente a associação a ser usada. A associação especificada é usada para resolver todas as referências de metadados.  
  
 Assim como qualquer outro cliente do Windows Communication Foundation (WCF), <xref:System.ServiceModel.Description.MetadataExchangeClient> o tipo fornece um construtor para carregar as configurações de ponto de extremidade do cliente usando o nome de configuração do ponto de extremidade. A configuração do ponto de extremidade especificado <xref:System.ServiceModel.Description.IMetadataExchange> deve especificar o contrato. O endereço na configuração do ponto de extremidade não é carregado, portanto, você deve usar <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> uma das sobrecargas que usam um endereço. Quando você especifica o endereço de metadados usando <xref:System.ServiceModel.EndpointAddress> uma instância, <xref:System.ServiceModel.Description.MetadataExchangeClient> o pressupõe que o endereço aponta para um ponto de extremidade MEX. Se você especificar o endereço de metadados como uma URL, também precisará especificar qual deles <xref:System.ServiceModel.Description.MetadataExchangeClientMode> usar, Mex ou http Get.  
  
> [!IMPORTANT]
> Por padrão, o <xref:System.ServiceModel.Description.MetadataExchangeClient> resolve todas as referências para você, incluindo WSDL e importações de esquema XML e inclui o. Você pode desabilitar essa funcionalidade definindo a <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> Propriedade como. `false` Você pode controlar o número máximo de referências a serem resolvidas <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> usando a propriedade. Você pode usar essa propriedade em conjunto com a `MaxReceivedMessageSize` Propriedade na associação para controlar a quantidade de metadados recuperados.  
  
### <a name="to-use-metadataexchangeclient-to-obtain-metadata"></a>Para usar o MetadataExchangeClient para obter metadados  
  
1. Crie um novo <xref:System.ServiceModel.Description.MetadataExchangeClient> objeto especificando explicitamente uma associação, um nome de configuração de ponto de extremidade ou o endereço dos metadados.  
  
2. Configure o <xref:System.ServiceModel.Description.MetadataExchangeClient> para atender às suas necessidades. Por exemplo, você pode especificar as credenciais a serem usadas ao solicitar metadados, controlar como as referências de metadados são resolvidas e definir a <xref:System.ServiceModel.Description.MetadataExchangeClient.OperationTimeout%2A> propriedade para controlar quanto tempo a solicitação de metadados deve retornar antes de expirar.  
  
3. Obtenha o <xref:System.ServiceModel.Description.MetadataSet> objeto que contém os metadados recuperados chamando um <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> dos métodos. Observe que você só poderá usar a <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> sobrecarga que não utilize nenhum argumento se você especificou explicitamente um endereço ao construir <xref:System.ServiceModel.Description.MetadataExchangeClient>o.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como <xref:System.ServiceModel.Description.MetadataExchangeClient> usar o para baixar e enumerar arquivos de metadados.  

 [!code-csharp[MetadataResolver#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/metadataresolver/cs/client.cs#3)]  

## <a name="compiling-the-code"></a>Compilando o código  
 Para compilar este exemplo de código, você deve fazer referência ao assembly System. ServiceModel. dll e <xref:System.ServiceModel.Description> importar o namespace.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Description.MetadataResolver>
- <xref:System.ServiceModel.Description.MetadataExchangeClient>
- <xref:System.ServiceModel.Description.WsdlImporter>
