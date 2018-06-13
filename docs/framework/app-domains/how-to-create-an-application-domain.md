---
title: Como criar um domínio de aplicativo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c579c97e273e7d3e149e04f7aa7670313663b617
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751760"
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="4d75e-102">Como criar um domínio de aplicativo</span><span class="sxs-lookup"><span data-stu-id="4d75e-102">How to: Create an Application Domain</span></span>
<span data-ttu-id="4d75e-103">Um host Common Language Runtime cria domínios de aplicativos automaticamente quando eles são necessários.</span><span class="sxs-lookup"><span data-stu-id="4d75e-103">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="4d75e-104">No entanto, você pode criar seus próprios domínios dos aplicativos e carregá-los nos assemblies que você deseja gerenciar pessoalmente.</span><span class="sxs-lookup"><span data-stu-id="4d75e-104">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="4d75e-105">Você também pode criar domínios do aplicativo do qual o código é executado.</span><span class="sxs-lookup"><span data-stu-id="4d75e-105">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="4d75e-106">Crie um novo domínio do aplicativo usando um dos métodos **CreateDomain** sobrecarregados na classe <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4d75e-106">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="4d75e-107">Você pode dar ao domínio do aplicativo um nome e referenciá-lo por esse nome.</span><span class="sxs-lookup"><span data-stu-id="4d75e-107">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="4d75e-108">O exemplo a seguir cria um novo domínio do aplicativo, atribui a ele o nome `MyDomain` e, em seguida, imprime o nome do domínio do host e o domínio do aplicativo filho recém-criado no console.</span><span class="sxs-lookup"><span data-stu-id="4d75e-108">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d75e-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d75e-109">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4d75e-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d75e-110">See Also</span></span>  
 [<span data-ttu-id="4d75e-111">Programação com domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="4d75e-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)  
 [<span data-ttu-id="4d75e-112">Usar domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="4d75e-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
