---
title: Como utilizar o MetadataExchangeClient para recuperar metadados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0754e9dc-13c5-45c2-81b5-f3da466e5a87
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 119e23c5834fdc646a793a4e84f191a37bca2f63
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-metadataexchangeclient-to-retrieve-metadata"></a>Como utilizar o MetadataExchangeClient para recuperar metadados
Use o <xref:System.ServiceModel.Description.MetadataExchangeClient> classe para baixar os metadados usando o protocolo WS-MetadataExchange (MEX). Os arquivos de metadados recuperados são retornados como um <xref:System.ServiceModel.Description.MetadataSet> objeto. Retornado <xref:System.ServiceModel.Description.MetadataSet> objeto contém uma coleção de <xref:System.ServiceModel.Description.MetadataSection> objetos, cada qual contendo um dialeto de metadados específico e um identificador. Você pode escrever os metadados retornados em arquivos ou, se os metadados retornados contém documentos WSDL Web Services Description Language (), você poderá importar os metadados usando o <xref:System.ServiceModel.Description.WsdlImporter>.  
  
 O <xref:System.ServiceModel.Description.MetadataExchangeClient> construtores que usam um endereço de usam a associação no <xref:System.ServiceModel.Description.MetadataExchangeBindings> classe estática que corresponda ao esquema de identificador de recurso uniforme (URI) do endereço. Como alternativa, você pode usar o <xref:System.ServiceModel.Description.MetadataExchangeClient> construtor que permite que você especifique explicitamente a associação a ser usada. A associação especificada é usada para resolver todas as referências de metadados.  
  
 Assim como qualquer outro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] cliente, o <xref:System.ServiceModel.Description.MetadataExchangeClient> tipo fornece um construtor para carregar as configurações de ponto de extremidade de cliente usando o nome de configuração do ponto de extremidade. A configuração de ponto de extremidade especificado deve especificar o <xref:System.ServiceModel.Description.IMetadataExchange> contrato. O endereço na configuração de ponto de extremidade não está carregado, você deve usar uma da <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> sobrecargas que têm um endereço. Quando você especifica o endereço de metadados usando um <xref:System.ServiceModel.EndpointAddress> instância, o <xref:System.ServiceModel.Description.MetadataExchangeClient> supõe que o endereço aponta para um ponto de extremidade MEX. Se você especificar o endereço de metadados como uma URL, você também precisa especificar qual <xref:System.ServiceModel.Description.MetadataExchangeClientMode> para usar, MEX ou HTTP GET.  
  
> [!IMPORTANT]
>  Por padrão, o <xref:System.ServiceModel.Description.MetadataExchangeClient> resolve todas as referências para você, incluindo WSDL e esquema XML importa e inclui. Você pode desabilitar essa funcionalidade, definindo o <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> propriedade `false`. Você pode controlar o número máximo de referências para resolver usando o <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> propriedade. Você pode usar essa propriedade em conjunto com o `MaxReceivedMessageSize` propriedade na associação para controlar como os metadados são recuperados.  
  
### <a name="to-use-metadataexchangeclient-to-obtain-metadata"></a>Para utilizar o MetadataExchangeClient para obter metadados  
  
1.  Criar um novo <xref:System.ServiceModel.Description.MetadataExchangeClient> objeto especificando explicitamente uma associação, um nome de configuração do ponto de extremidade ou o endereço de metadados.  
  
2.  Configurar o <xref:System.ServiceModel.Description.MetadataExchangeClient> para atender às suas necessidades. Por exemplo, você pode especificar as credenciais a usar quando se solicitam metadados controlam como referências de metadados são resolvidas e definir o <xref:System.ServiceModel.Description.MetadataExchangeClient.OperationTimeout%2A> propriedade para controlar quanto tempo a solicitação de metadados tem retornar antes de atingir o tempo limite.  
  
3.  Obter o <xref:System.ServiceModel.Description.MetadataSet> objeto que contém os metadados recuperados chamando um do <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> métodos. Observe que você só pode usar o <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> sobrecarga que não aceita argumentos se você especificou um endereço explicitamente ao construir o <xref:System.ServiceModel.Description.MetadataExchangeClient>.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como usar <xref:System.ServiceModel.Description.MetadataExchangeClient> para baixar e enumerar arquivos de metadados.  

 [!code-csharp[MetadataResolver#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/metadataresolver/cs/client.cs#3)]  

## <a name="compiling-the-code"></a>Compilando o código  
 Para compilar este exemplo de código, você deve fazer referência ao assembly System.ServiceModel.dll e importar o <xref:System.ServiceModel.Description> namespace.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.MetadataResolver>  
 <xref:System.ServiceModel.Description.MetadataExchangeClient>  
 <xref:System.ServiceModel.Description.WsdlImporter>
