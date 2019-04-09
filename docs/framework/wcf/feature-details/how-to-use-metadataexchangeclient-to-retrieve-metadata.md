---
title: 'Como: usar MetadataExchangeClient para recuperar metadados'
ms.date: 03/30/2017
ms.assetid: 0754e9dc-13c5-45c2-81b5-f3da466e5a87
ms.openlocfilehash: ec4177e71c7d46dc5c908f01a051dc5a0df6baa4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168610"
---
# <a name="how-to-use-metadataexchangeclient-to-retrieve-metadata"></a>Como: usar MetadataExchangeClient para recuperar metadados
Use o <xref:System.ServiceModel.Description.MetadataExchangeClient> classe para baixar os metadados usando o protocolo WS-MetadataExchange (MEX). Os arquivos de metadados recuperados são retornados como um <xref:System.ServiceModel.Description.MetadataSet> objeto. Retornado <xref:System.ServiceModel.Description.MetadataSet> objeto contém uma coleção de <xref:System.ServiceModel.Description.MetadataSection> objetos, cada um deles contendo um dialeto de metadados específicas e um identificador. Você pode gravar os metadados retornados em arquivos ou, se os metadados retornados contém documentos de descrição linguagem WSDL (Web Services), você pode importar os metadados usando o <xref:System.ServiceModel.Description.WsdlImporter>.  
  
 O <xref:System.ServiceModel.Description.MetadataExchangeClient> construtores que usam um endereço de usam a associação no <xref:System.ServiceModel.Description.MetadataExchangeBindings> classe estática que coincidir com o esquema de identificador de recurso uniforme (URI) do endereço. Como alternativa, você pode usar o <xref:System.ServiceModel.Description.MetadataExchangeClient> construtor que permite que você especifique explicitamente a associação a ser usada. A associação especificada é usada para resolver todas as referências de metadados.  
  
 Assim como qualquer outro cliente do Windows Communication Foundation (WCF), o <xref:System.ServiceModel.Description.MetadataExchangeClient> tipo fornece um construtor para carregar configurações de ponto de extremidade de cliente usando o nome da configuração de ponto de extremidade. A configuração de ponto de extremidade especificado deve especificar o <xref:System.ServiceModel.Description.IMetadataExchange> contrato. O endereço na configuração do ponto de extremidade não está carregado, portanto, você deve usar um do <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> sobrecargas que usam um endereço. Quando você especifica o endereço de metadados usando um <xref:System.ServiceModel.EndpointAddress> instância, o <xref:System.ServiceModel.Description.MetadataExchangeClient> pressupõe que o endereço aponta para um ponto de extremidade MEX. Se você especificar o endereço de metadados como uma URL, você também precisa especificar qual <xref:System.ServiceModel.Description.MetadataExchangeClientMode> de usar, MEX ou HTTP GET.  
  
> [!IMPORTANT]
>  Por padrão, o <xref:System.ServiceModel.Description.MetadataExchangeClient> resolve todas as referências para você, incluindo o WSDL e esquema XML importa e inclui. Você pode desabilitar essa funcionalidade, definindo o <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> propriedade para `false`. Você pode controlar o número máximo de referências para resolver usando o <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> propriedade. Você pode usar essa propriedade em conjunto com o `MaxReceivedMessageSize` propriedade na associação para controlar quanto os metadados são recuperados.  
  
### <a name="to-use-metadataexchangeclient-to-obtain-metadata"></a>Para usar o MetadataExchangeClient para obter metadados  
  
1.  Criar um novo <xref:System.ServiceModel.Description.MetadataExchangeClient> objeto especificando explicitamente uma associação, um nome de configuração do ponto de extremidade ou o endereço dos metadados.  
  
2.  Configurar o <xref:System.ServiceModel.Description.MetadataExchangeClient> para atender às suas necessidades. Por exemplo, você pode especificar credenciais para usar ao solicitar metadados, controlar como referências de metadados são resolvidas e definir o <xref:System.ServiceModel.Description.MetadataExchangeClient.OperationTimeout%2A> propriedade para controlar quanto tempo a solicitação de metadados tem retornar antes de atingir o tempo limite.  
  
3.  Obter o <xref:System.ServiceModel.Description.MetadataSet> objeto que contém os metadados recuperados chamando um do <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> métodos. Observe que você só pode usar o <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> sobrecarga que não usa nenhum argumento se for especificado explicitamente um endereço ao construir o <xref:System.ServiceModel.Description.MetadataExchangeClient>.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como usar <xref:System.ServiceModel.Description.MetadataExchangeClient> para baixar e enumerar arquivos de metadados.  

 [!code-csharp[MetadataResolver#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/metadataresolver/cs/client.cs#3)]  

## <a name="compiling-the-code"></a>Compilando o código  
 Para compilar este exemplo de código, você deve fazer referência ao assembly de ServiceModel e importar o <xref:System.ServiceModel.Description> namespace.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Description.MetadataResolver>
- <xref:System.ServiceModel.Description.MetadataExchangeClient>
- <xref:System.ServiceModel.Description.WsdlImporter>
