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
ms.openlocfilehash: 84e38451f10acc341642c0bf0923cc73b79d771f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497926"
---
# <a name="version-tolerant-serialization-callbacks"></a><span data-ttu-id="4989e-102">Retornos de chamada de serialização tolerantes à versão</span><span class="sxs-lookup"><span data-stu-id="4989e-102">Version-Tolerant Serialization Callbacks</span></span>
<span data-ttu-id="4989e-103">O modelo de programação de contrato de dados suporta totalmente os métodos de retorno de chamada de serialização tolerantes à versão que o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> e <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes de suporte.</span><span class="sxs-lookup"><span data-stu-id="4989e-103">The data contract programming model fully supports the version-tolerant serialization callback methods that the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes support.</span></span>  
  
## <a name="version-tolerant-attributes"></a><span data-ttu-id="4989e-104">Atributos tolerantes à versão</span><span class="sxs-lookup"><span data-stu-id="4989e-104">Version-Tolerant Attributes</span></span>  
 <span data-ttu-id="4989e-105">Há quatro atributos de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="4989e-105">There are four callback attributes.</span></span> <span data-ttu-id="4989e-106">Cada atributo pode ser aplicado a um método que chama o mecanismo de serialização/desserialização várias vezes.</span><span class="sxs-lookup"><span data-stu-id="4989e-106">Each attribute can be applied to a method that the serialization/deserialization engine calls at various times.</span></span> <span data-ttu-id="4989e-107">A tabela a seguir explica quando usar cada atributo.</span><span class="sxs-lookup"><span data-stu-id="4989e-107">The table below explains when to use each attribute.</span></span>  
  
|<span data-ttu-id="4989e-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="4989e-108">Attribute</span></span>|<span data-ttu-id="4989e-109">Quando o método correspondente é chamado</span><span class="sxs-lookup"><span data-stu-id="4989e-109">When the corresponding method is called</span></span>|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="4989e-110">Chamado antes de serializar o tipo.</span><span class="sxs-lookup"><span data-stu-id="4989e-110">Called before serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="4989e-111">Chamado após a serialização do tipo.</span><span class="sxs-lookup"><span data-stu-id="4989e-111">Called after serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="4989e-112">Chamado antes de desserializar o tipo.</span><span class="sxs-lookup"><span data-stu-id="4989e-112">Called before deserializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="4989e-113">Chamado após a desserialização do tipo.</span><span class="sxs-lookup"><span data-stu-id="4989e-113">Called after deserializing the type.</span></span>|  
  
 <span data-ttu-id="4989e-114">Os métodos devem aceitar um <xref:System.Runtime.Serialization.StreamingContext> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4989e-114">The methods must accept a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span>  
  
 <span data-ttu-id="4989e-115">Esses métodos são principalmente para uso com controle de versão ou de inicialização.</span><span class="sxs-lookup"><span data-stu-id="4989e-115">These methods are primarily intended for use with versioning or initialization.</span></span> <span data-ttu-id="4989e-116">Durante a desserialização, não é chamados de nenhum construtor.</span><span class="sxs-lookup"><span data-stu-id="4989e-116">During deserialization, no constructors are called.</span></span> <span data-ttu-id="4989e-117">Portanto, os membros de dados podem não ser inicializados corretamente (para valores padrão pretendido) se os dados para esses membros estão ausentes no fluxo de entrada, por exemplo, se os dados vêm de uma versão anterior de um tipo que não tem alguns membros de dados.</span><span class="sxs-lookup"><span data-stu-id="4989e-117">Therefore, data members may not be correctly initialized (to intended default values) if the data for these members is missing in the incoming stream, for example, if the data comes from a previous version of a type that is missing some data members.</span></span> <span data-ttu-id="4989e-118">Para corrigir isso, use o método de retorno de chamada marcado com o <xref:System.Runtime.Serialization.OnDeserializingAttribute>, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4989e-118">To correct this, use the callback method marked with the <xref:System.Runtime.Serialization.OnDeserializingAttribute>, as shown in the following example.</span></span>  
  
 <span data-ttu-id="4989e-119">Você pode marcar apenas um método por tipo, com cada um dos atributos precedentes de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="4989e-119">You can mark only one method per type with each of the preceding callback attributes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="4989e-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4989e-120">Example</span></span>  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="4989e-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4989e-121">See Also</span></span>  
 <xref:System.Runtime.Serialization.OnSerializingAttribute>  
 <xref:System.Runtime.Serialization.OnSerializedAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
 <xref:System.Runtime.Serialization.StreamingContext>  
 [<span data-ttu-id="4989e-122">Serialização tolerante a versão</span><span class="sxs-lookup"><span data-stu-id="4989e-122">Version Tolerant Serialization</span></span>](../../../../docs/standard/serialization/version-tolerant-serialization.md)
