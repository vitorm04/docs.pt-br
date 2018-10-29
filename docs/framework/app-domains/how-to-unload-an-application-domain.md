---
title: Como descarregar um domínio de aplicativo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8b4cbdff72167cfc063254cf5370d22fb729b0a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50088566"
---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="53d33-102">Como descarregar um domínio de aplicativo</span><span class="sxs-lookup"><span data-stu-id="53d33-102">How to: Unload an Application Domain</span></span>
<span data-ttu-id="53d33-103">Quando terminar de usar um domínio do aplicativo, descarregue-o usando o método <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="53d33-103">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="53d33-104">O método **Unload** desliga normalmente o domínio de aplicativo especificado.</span><span class="sxs-lookup"><span data-stu-id="53d33-104">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="53d33-105">Durante o processo de descarga, nenhum thread novo pode acessar o domínio do aplicativo e todas as estruturas de dados específicas do domínio do aplicativo são liberadas.</span><span class="sxs-lookup"><span data-stu-id="53d33-105">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="53d33-106">Os assemblies carregados no domínio do aplicativo são removidos e não ficam mais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="53d33-106">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="53d33-107">Se um assembly no domínio do aplicativo forem independentes de domínio, os dados para o assembly permanecerão na memória até que todo o processo seja desligado.</span><span class="sxs-lookup"><span data-stu-id="53d33-107">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="53d33-108">Não há outro mecanismo para descarregar um assembly com neutralidade de domínio a não ser desligar o processo inteiro.</span><span class="sxs-lookup"><span data-stu-id="53d33-108">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="53d33-109">Há situações em que a solicitação para descarregar um domínio do aplicativo não funciona e resulta em uma <xref:System.CannotUnloadAppDomainException>.</span><span class="sxs-lookup"><span data-stu-id="53d33-109">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="53d33-110">O exemplo a seguir cria um novo domínio do aplicativo chamado `MyDomain`, imprime algumas informações no console e descarrega o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53d33-110">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="53d33-111">Observe que o código tenta imprimir o nome amigável do domínio do aplicativo descarregado no console.</span><span class="sxs-lookup"><span data-stu-id="53d33-111">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="53d33-112">Essa ação gera uma exceção que é manipulada pelas instruções try/catch no fim do programa.</span><span class="sxs-lookup"><span data-stu-id="53d33-112">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53d33-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="53d33-113">Example</span></span>  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="53d33-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53d33-114">See Also</span></span>  
- [<span data-ttu-id="53d33-115">Programação com domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="53d33-115">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)  
- [<span data-ttu-id="53d33-116">Como criar um domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="53d33-116">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
- [<span data-ttu-id="53d33-117">Usar domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="53d33-117">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
