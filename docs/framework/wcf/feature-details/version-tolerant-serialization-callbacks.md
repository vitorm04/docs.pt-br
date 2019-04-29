---
title: Retornos de chamada de serialização tolerantes à versão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OnDeserializedAttribute [WCF]
- OnDeserializingAttribute [WCF]
- OnSerializingAttribute [WCF]
- serialization [WCF], setting default values
- OnSerializedAttribute [WCF]
ms.assetid: aa4a3a6f-05ec-4efd-bdbf-2181e13e6468
ms.openlocfilehash: da13f9989b427da047c4a94f77907847ed2ae4d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61932620"
---
# <a name="version-tolerant-serialization-callbacks"></a><span data-ttu-id="ccabe-102">Retornos de chamada de serialização tolerantes à versão</span><span class="sxs-lookup"><span data-stu-id="ccabe-102">Version-Tolerant Serialization Callbacks</span></span>
<span data-ttu-id="ccabe-103">O modelo de programação de contrato de dados totalmente compatível com os métodos de retorno de chamada de serialização tolerantes à versão que o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> e <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes oferecem suporte.</span><span class="sxs-lookup"><span data-stu-id="ccabe-103">The data contract programming model fully supports the version-tolerant serialization callback methods that the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes support.</span></span>  
  
## <a name="version-tolerant-attributes"></a><span data-ttu-id="ccabe-104">Atributos tolerantes à versão</span><span class="sxs-lookup"><span data-stu-id="ccabe-104">Version-Tolerant Attributes</span></span>  
 <span data-ttu-id="ccabe-105">Há quatro atributos de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="ccabe-105">There are four callback attributes.</span></span> <span data-ttu-id="ccabe-106">Cada atributo pode ser aplicado a um método que o mecanismo de serialização/desserialização chama em vários momentos.</span><span class="sxs-lookup"><span data-stu-id="ccabe-106">Each attribute can be applied to a method that the serialization/deserialization engine calls at various times.</span></span> <span data-ttu-id="ccabe-107">A tabela a seguir explica quando usar cada atributo.</span><span class="sxs-lookup"><span data-stu-id="ccabe-107">The table below explains when to use each attribute.</span></span>  
  
|<span data-ttu-id="ccabe-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="ccabe-108">Attribute</span></span>|<span data-ttu-id="ccabe-109">Quando o método correspondente é chamado</span><span class="sxs-lookup"><span data-stu-id="ccabe-109">When the corresponding method is called</span></span>|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="ccabe-110">Chamado antes de serializar o tipo.</span><span class="sxs-lookup"><span data-stu-id="ccabe-110">Called before serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="ccabe-111">Chamado depois de serializar o tipo.</span><span class="sxs-lookup"><span data-stu-id="ccabe-111">Called after serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="ccabe-112">Chamado antes de desserializar o tipo.</span><span class="sxs-lookup"><span data-stu-id="ccabe-112">Called before deserializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="ccabe-113">Chamado depois de desserializar o tipo.</span><span class="sxs-lookup"><span data-stu-id="ccabe-113">Called after deserializing the type.</span></span>|  
  
 <span data-ttu-id="ccabe-114">Os métodos devem aceitar uma <xref:System.Runtime.Serialization.StreamingContext> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ccabe-114">The methods must accept a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span>  
  
 <span data-ttu-id="ccabe-115">Esses métodos destinam-se principalmente para uso com o controle de versão ou de inicialização.</span><span class="sxs-lookup"><span data-stu-id="ccabe-115">These methods are primarily intended for use with versioning or initialization.</span></span> <span data-ttu-id="ccabe-116">Durante a desserialização, nenhum construtor é chamado.</span><span class="sxs-lookup"><span data-stu-id="ccabe-116">During deserialization, no constructors are called.</span></span> <span data-ttu-id="ccabe-117">Portanto, os membros de dados podem não ser inicializados corretamente (para valores padrão pretendido) se os dados para esses membros estão ausentes no fluxo de entrada, por exemplo, se os dados vêm de uma versão anterior de um tipo que está faltando alguns membros de dados.</span><span class="sxs-lookup"><span data-stu-id="ccabe-117">Therefore, data members may not be correctly initialized (to intended default values) if the data for these members is missing in the incoming stream, for example, if the data comes from a previous version of a type that is missing some data members.</span></span> <span data-ttu-id="ccabe-118">Para corrigir isso, use o método de retorno de chamada marcado com o <xref:System.Runtime.Serialization.OnDeserializingAttribute>, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ccabe-118">To correct this, use the callback method marked with the <xref:System.Runtime.Serialization.OnDeserializingAttribute>, as shown in the following example.</span></span>  
  
 <span data-ttu-id="ccabe-119">Você pode marcar apenas um método por tipo, com cada um dos atributos precedentes do retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="ccabe-119">You can mark only one method per type with each of the preceding callback attributes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="ccabe-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ccabe-120">Example</span></span>  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="ccabe-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ccabe-121">See also</span></span>

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [<span data-ttu-id="ccabe-122">Serialização tolerante a versão</span><span class="sxs-lookup"><span data-stu-id="ccabe-122">Version Tolerant Serialization</span></span>](../../../../docs/standard/serialization/version-tolerant-serialization.md)
