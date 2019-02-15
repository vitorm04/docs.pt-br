---
title: 'Como: Usar vários Tokens de segurança do mesmo tipo'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
ms.openlocfilehash: a532d40d8c31894c63a382ecad0cbcf8b42e3a66
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303758"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="0a9fe-102">Como: Usar vários Tokens de segurança do mesmo tipo</span><span class="sxs-lookup"><span data-stu-id="0a9fe-102">How to: Use Multiple Security Tokens of the Same Type</span></span>
-   <span data-ttu-id="0a9fe-103">No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, um token de cliente de mensagem somente deles independente de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="0a9fe-103">In [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="0a9fe-104">Agora, as mensagens do cliente podem conter vários tokens de um tipo.</span><span class="sxs-lookup"><span data-stu-id="0a9fe-104">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="0a9fe-105">Este tópico mostra como incluir vários tokens do mesmo tipo em uma mensagem do cliente.</span><span class="sxs-lookup"><span data-stu-id="0a9fe-105">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
-   <span data-ttu-id="0a9fe-106">Observe que você não pode configurar um serviço dessa maneira: um serviço pode conter apenas um token de suporte.</span><span class="sxs-lookup"><span data-stu-id="0a9fe-106">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="0a9fe-107">Para usar vários tokens de segurança do mesmo tipo</span><span class="sxs-lookup"><span data-stu-id="0a9fe-107">To use multiple security tokens of the same type</span></span>  
  
1.  <span data-ttu-id="0a9fe-108">Crie uma coleção de elementos de associação vazia a ser preenchido.</span><span class="sxs-lookup"><span data-stu-id="0a9fe-108">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2.  <span data-ttu-id="0a9fe-109">Criar uma <xref:System.ServiceModel.Channels.SecurityBindingElement> chamando <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="0a9fe-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3.  <span data-ttu-id="0a9fe-110">Criar um <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> coleção.</span><span class="sxs-lookup"><span data-stu-id="0a9fe-110">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4.  <span data-ttu-id="0a9fe-111">Adicione tokens SAML à coleção.</span><span class="sxs-lookup"><span data-stu-id="0a9fe-111">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5.  <span data-ttu-id="0a9fe-112">Adicionar a coleção para a <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="0a9fe-112">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6.  <span data-ttu-id="0a9fe-113">Adicione elementos de associação para a coleção de elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="0a9fe-113">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7.  <span data-ttu-id="0a9fe-114">Retorne uma nova associação personalizada criada da coleção do elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="0a9fe-114">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="0a9fe-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0a9fe-115">Example</span></span>  
 <span data-ttu-id="0a9fe-116">Este é todo o método descrito pelo procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="0a9fe-116">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
