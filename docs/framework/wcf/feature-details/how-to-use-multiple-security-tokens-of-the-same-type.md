---
title: Como usar vários tokens de segurança do mesmo tipo
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 67a9fd51377294ab6afb5a3d7deaec19fb134b21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490741"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="d8e38-102">Como usar vários tokens de segurança do mesmo tipo</span><span class="sxs-lookup"><span data-stu-id="d8e38-102">How to: Use Multiple Security Tokens of the Same Type</span></span>
-   <span data-ttu-id="d8e38-103">Em [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, um token de mensagem somente um independente do cliente de qualquer tipo determinado.</span><span class="sxs-lookup"><span data-stu-id="d8e38-103">In [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="d8e38-104">Agora as mensagens de cliente podem conter vários tokens de um tipo.</span><span class="sxs-lookup"><span data-stu-id="d8e38-104">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="d8e38-105">Este tópico mostra como incluir vários tokens do mesmo tipo em uma mensagem do cliente.</span><span class="sxs-lookup"><span data-stu-id="d8e38-105">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
-   <span data-ttu-id="d8e38-106">Observe que você não pode configurar um serviço dessa forma: um serviço pode conter apenas um token de suporte.</span><span class="sxs-lookup"><span data-stu-id="d8e38-106">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="d8e38-107">Para usar vários tokens de segurança do mesmo tipo</span><span class="sxs-lookup"><span data-stu-id="d8e38-107">To use multiple security tokens of the same type</span></span>  
  
1.  <span data-ttu-id="d8e38-108">Crie uma coleção de elementos de associação vazio a ser preenchido.</span><span class="sxs-lookup"><span data-stu-id="d8e38-108">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2.  <span data-ttu-id="d8e38-109">Criar um <xref:System.ServiceModel.Channels.SecurityBindingElement> chamando <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="d8e38-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3.  <span data-ttu-id="d8e38-110">Criar um <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> coleção.</span><span class="sxs-lookup"><span data-stu-id="d8e38-110">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4.  <span data-ttu-id="d8e38-111">Adicione tokens SAML à coleção.</span><span class="sxs-lookup"><span data-stu-id="d8e38-111">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5.  <span data-ttu-id="d8e38-112">Adicionar a coleção para a <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="d8e38-112">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6.  <span data-ttu-id="d8e38-113">Adicione elementos de associação para a coleção de elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="d8e38-113">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7.  <span data-ttu-id="d8e38-114">Retorna uma nova associação personalizada criada a partir de coleção de elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="d8e38-114">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="d8e38-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d8e38-115">Example</span></span>  
 <span data-ttu-id="d8e38-116">A seguir está a todo o método descrito pelo procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="d8e38-116">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
  
## <a name="see-also"></a><span data-ttu-id="d8e38-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8e38-117">See Also</span></span>  
 [<span data-ttu-id="d8e38-118">Arquitetura de segurança</span><span class="sxs-lookup"><span data-stu-id="d8e38-118">Security Architecture</span></span>](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
