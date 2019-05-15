---
title: 'Como: usar vários tokens de segurança do mesmo tipo'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
ms.openlocfilehash: 1b383c6ccd96d1b3d7b091b2d7c67bb166da51df
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589424"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="862cb-102">Como: usar vários tokens de segurança do mesmo tipo</span><span class="sxs-lookup"><span data-stu-id="862cb-102">How to: Use Multiple Security Tokens of the Same Type</span></span>
- <span data-ttu-id="862cb-103">No .NET Framework 3.0, uma mensagem de cliente continha somente um token de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="862cb-103">In .NET Framework 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="862cb-104">Agora, as mensagens do cliente podem conter vários tokens de um tipo.</span><span class="sxs-lookup"><span data-stu-id="862cb-104">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="862cb-105">Este tópico mostra como incluir vários tokens do mesmo tipo em uma mensagem do cliente.</span><span class="sxs-lookup"><span data-stu-id="862cb-105">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
- <span data-ttu-id="862cb-106">Observe que você não pode configurar um serviço dessa maneira: um serviço pode conter apenas um token de suporte.</span><span class="sxs-lookup"><span data-stu-id="862cb-106">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="862cb-107">Para usar vários tokens de segurança do mesmo tipo</span><span class="sxs-lookup"><span data-stu-id="862cb-107">To use multiple security tokens of the same type</span></span>  
  
1. <span data-ttu-id="862cb-108">Crie uma coleção de elementos de associação vazia a ser preenchido.</span><span class="sxs-lookup"><span data-stu-id="862cb-108">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2. <span data-ttu-id="862cb-109">Criar uma <xref:System.ServiceModel.Channels.SecurityBindingElement> chamando <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="862cb-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3. <span data-ttu-id="862cb-110">Criar um <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> coleção.</span><span class="sxs-lookup"><span data-stu-id="862cb-110">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4. <span data-ttu-id="862cb-111">Adicione tokens SAML à coleção.</span><span class="sxs-lookup"><span data-stu-id="862cb-111">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5. <span data-ttu-id="862cb-112">Adicionar a coleção para a <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="862cb-112">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6. <span data-ttu-id="862cb-113">Adicione elementos de associação para a coleção de elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="862cb-113">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7. <span data-ttu-id="862cb-114">Retorne uma nova associação personalizada criada da coleção do elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="862cb-114">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="862cb-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="862cb-115">Example</span></span>  
 <span data-ttu-id="862cb-116">Este é todo o método descrito pelo procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="862cb-116">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
