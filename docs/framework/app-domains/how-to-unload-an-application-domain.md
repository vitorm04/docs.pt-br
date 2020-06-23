---
title: 'Como: Descarregar um domínio do aplicativo'
description: Leia como descarregar um domínio de aplicativo no .NET usando o método AppDomain. Unload para desligar o domínio do aplicativo especificado normalmente.
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
ms.openlocfilehash: b64a9553f63aa4a8deb57f23a97fa464edd64fee
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104669"
---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="c2c79-103">Como: Descarregar um domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="c2c79-103">How to: Unload an Application Domain</span></span>
<span data-ttu-id="c2c79-104">Quando terminar de usar um domínio do aplicativo, descarregue-o usando o método <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c2c79-104">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c2c79-105">O método **Unload** desliga normalmente o domínio de aplicativo especificado.</span><span class="sxs-lookup"><span data-stu-id="c2c79-105">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="c2c79-106">Durante o processo de descarga, nenhum thread novo pode acessar o domínio do aplicativo e todas as estruturas de dados específicas do domínio do aplicativo são liberadas.</span><span class="sxs-lookup"><span data-stu-id="c2c79-106">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="c2c79-107">Os assemblies carregados no domínio do aplicativo são removidos e não ficam mais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c2c79-107">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="c2c79-108">Se um assembly no domínio do aplicativo forem independentes de domínio, os dados para o assembly permanecerão na memória até que todo o processo seja desligado.</span><span class="sxs-lookup"><span data-stu-id="c2c79-108">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="c2c79-109">Não há outro mecanismo para descarregar um assembly com neutralidade de domínio a não ser desligar o processo inteiro.</span><span class="sxs-lookup"><span data-stu-id="c2c79-109">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="c2c79-110">Há situações em que a solicitação para descarregar um domínio do aplicativo não funciona e resulta em uma <xref:System.CannotUnloadAppDomainException>.</span><span class="sxs-lookup"><span data-stu-id="c2c79-110">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="c2c79-111">O exemplo a seguir cria um novo domínio do aplicativo chamado `MyDomain`, imprime algumas informações no console e descarrega o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c2c79-111">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="c2c79-112">Observe que o código tenta imprimir o nome amigável do domínio do aplicativo descarregado no console.</span><span class="sxs-lookup"><span data-stu-id="c2c79-112">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="c2c79-113">Essa ação gera uma exceção que é manipulada pelas instruções try/catch no fim do programa.</span><span class="sxs-lookup"><span data-stu-id="c2c79-113">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2c79-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c2c79-114">Example</span></span>  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c2c79-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="c2c79-115">See also</span></span>

- [<span data-ttu-id="c2c79-116">Programação com domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="c2c79-116">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="c2c79-117">Como: Criar um domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="c2c79-117">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)
- [<span data-ttu-id="c2c79-118">Usando domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="c2c79-118">Using Application Domains</span></span>](use.md)
