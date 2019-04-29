---
title: 'Como: desabilitar sessões seguras em uma WSFederationHttpBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
ms.openlocfilehash: 38863cbfe457afd923c3c8238d8c12b4d451c67f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773081"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a><span data-ttu-id="b9df1-102">Como: desabilitar sessões seguras em uma WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="b9df1-102">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>
<span data-ttu-id="b9df1-103">Alguns serviços podem exigir credenciais federadas, mas não dá suporte a sessões seguras.</span><span class="sxs-lookup"><span data-stu-id="b9df1-103">Some services may require federated credentials but not support secure sessions.</span></span> <span data-ttu-id="b9df1-104">Nesse caso, você deve desabilitar o recurso de sessão segura.</span><span class="sxs-lookup"><span data-stu-id="b9df1-104">In that case, you must disable the secure session feature.</span></span> <span data-ttu-id="b9df1-105">Ao contrário do <xref:System.ServiceModel.WSHttpBinding>, o <xref:System.ServiceModel.WSFederationHttpBinding> classe não fornece uma maneira de desabilitar sessões seguras ao se comunicar com um serviço.</span><span class="sxs-lookup"><span data-stu-id="b9df1-105">Unlike the <xref:System.ServiceModel.WSHttpBinding>, the <xref:System.ServiceModel.WSFederationHttpBinding> class does not provide a way to disable secure sessions when communicating with a service.</span></span> <span data-ttu-id="b9df1-106">Em vez disso, você deve criar uma associação personalizada que substitui as configurações de sessão segura com um bootstrap.</span><span class="sxs-lookup"><span data-stu-id="b9df1-106">Instead, you must create a custom binding that replaces the secure session settings with a bootstrap.</span></span>  
  
 <span data-ttu-id="b9df1-107">Este tópico demonstra como modificar os elementos de associação contidos em um <xref:System.ServiceModel.WSFederationHttpBinding> para criar uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="b9df1-107">This topic demonstrates how to modify the binding elements contained within a <xref:System.ServiceModel.WSFederationHttpBinding> to create a custom binding.</span></span> <span data-ttu-id="b9df1-108">O resultado é idêntico de <xref:System.ServiceModel.WSFederationHttpBinding> , exceto que ele não usa sessões seguras.</span><span class="sxs-lookup"><span data-stu-id="b9df1-108">The result is identical to the <xref:System.ServiceModel.WSFederationHttpBinding> except that it does not use secure sessions.</span></span>  
  
### <a name="to-create-a-custom-federated-binding-without-secure-session"></a><span data-ttu-id="b9df1-109">Para criar um personalizado federado associação sem sessão segura</span><span class="sxs-lookup"><span data-stu-id="b9df1-109">To create a custom federated binding without secure session</span></span>  
  
1. <span data-ttu-id="b9df1-110">Criar uma instância da <xref:System.ServiceModel.WSFederationHttpBinding> classe imperativa no código ou carregando um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="b9df1-110">Create an instance of the <xref:System.ServiceModel.WSFederationHttpBinding> class either imperatively in code or by loading one from the configuration file.</span></span>  
  
2. <span data-ttu-id="b9df1-111">Clone o <xref:System.ServiceModel.WSFederationHttpBinding> em um <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="b9df1-111">Clone the <xref:System.ServiceModel.WSFederationHttpBinding> into a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
3. <span data-ttu-id="b9df1-112">Localizar o <xref:System.ServiceModel.Channels.SecurityBindingElement> no <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="b9df1-112">Find the <xref:System.ServiceModel.Channels.SecurityBindingElement> in the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
4. <span data-ttu-id="b9df1-113">Localizar o <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> no <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="b9df1-113">Find the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> in the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
5. <span data-ttu-id="b9df1-114">Substituir o original <xref:System.ServiceModel.Channels.SecurityBindingElement> com o elemento de associação de segurança de inicialização do <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span><span class="sxs-lookup"><span data-stu-id="b9df1-114">Replace the original <xref:System.ServiceModel.Channels.SecurityBindingElement> with the bootstrap security binding element from the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9df1-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b9df1-115">Example</span></span>  
 <span data-ttu-id="b9df1-116">Este exemplo a seguir cria uma associação personalizada federada sem sessão segura.</span><span class="sxs-lookup"><span data-stu-id="b9df1-116">This following example creates a custom federated binding without secure session.</span></span>  
  
 [!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
 [!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b9df1-117">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b9df1-117">Compiling the Code</span></span>  
  
- <span data-ttu-id="b9df1-118">Para compilar o exemplo de código, crie um projeto que referencia o assembly de ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="b9df1-118">To compile the code example, create a project that references the System.ServiceModel.dll assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9df1-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9df1-119">See also</span></span>

- [<span data-ttu-id="b9df1-120">Associações e segurança</span><span class="sxs-lookup"><span data-stu-id="b9df1-120">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
