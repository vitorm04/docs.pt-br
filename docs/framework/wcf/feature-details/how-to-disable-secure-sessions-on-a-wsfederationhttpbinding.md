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
ms.openlocfilehash: 810c5b127a34fb0a35e8fd2d83ff59e00aca0ba1
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972041"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a><span data-ttu-id="1a2bf-102">Como: desabilitar sessões seguras em uma WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="1a2bf-102">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>

<span data-ttu-id="1a2bf-103">Alguns serviços podem exigir credenciais federadas, mas não dar suporte a sessões seguras.</span><span class="sxs-lookup"><span data-stu-id="1a2bf-103">Some services may require federated credentials but not support secure sessions.</span></span> <span data-ttu-id="1a2bf-104">Nesse caso, você deve desabilitar o recurso de sessão segura.</span><span class="sxs-lookup"><span data-stu-id="1a2bf-104">In that case, you must disable the secure session feature.</span></span> <span data-ttu-id="1a2bf-105">Ao contrário <xref:System.ServiceModel.WSHttpBinding>do, <xref:System.ServiceModel.WSFederationHttpBinding> a classe não fornece uma maneira de desabilitar sessões seguras ao se comunicar com um serviço.</span><span class="sxs-lookup"><span data-stu-id="1a2bf-105">Unlike the <xref:System.ServiceModel.WSHttpBinding>, the <xref:System.ServiceModel.WSFederationHttpBinding> class does not provide a way to disable secure sessions when communicating with a service.</span></span> <span data-ttu-id="1a2bf-106">Em vez disso, você deve criar uma associação personalizada que substitua as configurações de sessão segura por uma inicialização.</span><span class="sxs-lookup"><span data-stu-id="1a2bf-106">Instead, you must create a custom binding that replaces the secure session settings with a bootstrap.</span></span>

<span data-ttu-id="1a2bf-107">Este tópico demonstra como modificar os elementos de associação contidos em um <xref:System.ServiceModel.WSFederationHttpBinding> para criar uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="1a2bf-107">This topic demonstrates how to modify the binding elements contained within a <xref:System.ServiceModel.WSFederationHttpBinding> to create a custom binding.</span></span> <span data-ttu-id="1a2bf-108">O resultado é idêntico ao <xref:System.ServiceModel.WSFederationHttpBinding> , exceto que ele não usa sessões seguras.</span><span class="sxs-lookup"><span data-stu-id="1a2bf-108">The result is identical to the <xref:System.ServiceModel.WSFederationHttpBinding> except that it does not use secure sessions.</span></span>

## <a name="to-create-a-custom-federated-binding-without-secure-session"></a><span data-ttu-id="1a2bf-109">Para criar uma associação federada personalizada sem sessão segura</span><span class="sxs-lookup"><span data-stu-id="1a2bf-109">To create a custom federated binding without secure session</span></span>

1. <span data-ttu-id="1a2bf-110">Crie uma instância da <xref:System.ServiceModel.WSFederationHttpBinding> classe de forma imperativa no código ou carregando uma do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="1a2bf-110">Create an instance of the <xref:System.ServiceModel.WSFederationHttpBinding> class either imperatively in code or by loading one from the configuration file.</span></span>

2. <span data-ttu-id="1a2bf-111">Clone o <xref:System.ServiceModel.WSFederationHttpBinding> em um <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="1a2bf-111">Clone the <xref:System.ServiceModel.WSFederationHttpBinding> into a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>

3. <span data-ttu-id="1a2bf-112">Localize o <xref:System.ServiceModel.Channels.SecurityBindingElement> <xref:System.ServiceModel.Channels.CustomBinding>no.</span><span class="sxs-lookup"><span data-stu-id="1a2bf-112">Find the <xref:System.ServiceModel.Channels.SecurityBindingElement> in the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>

4. <span data-ttu-id="1a2bf-113">Localize o <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> <xref:System.ServiceModel.Channels.SecurityBindingElement>no.</span><span class="sxs-lookup"><span data-stu-id="1a2bf-113">Find the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> in the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>

5. <span data-ttu-id="1a2bf-114">Substitua o original <xref:System.ServiceModel.Channels.SecurityBindingElement> pelo elemento de associação <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>de segurança de bootstrap do.</span><span class="sxs-lookup"><span data-stu-id="1a2bf-114">Replace the original <xref:System.ServiceModel.Channels.SecurityBindingElement> with the bootstrap security binding element from the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span></span>

## <a name="example"></a><span data-ttu-id="1a2bf-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1a2bf-115">Example</span></span>

<span data-ttu-id="1a2bf-116">Este exemplo a seguir cria uma associação federada personalizada sem sessão segura.</span><span class="sxs-lookup"><span data-stu-id="1a2bf-116">This following example creates a custom federated binding without secure session.</span></span>

[!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
[!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="1a2bf-117">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="1a2bf-117">Compiling the Code</span></span>

- <span data-ttu-id="1a2bf-118">Para compilar o exemplo de código, crie um projeto que referencie o assembly System. ServiceModel. dll.</span><span class="sxs-lookup"><span data-stu-id="1a2bf-118">To compile the code example, create a project that references the System.ServiceModel.dll assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a2bf-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a2bf-119">See also</span></span>

- [<span data-ttu-id="1a2bf-120">Associações e segurança</span><span class="sxs-lookup"><span data-stu-id="1a2bf-120">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
