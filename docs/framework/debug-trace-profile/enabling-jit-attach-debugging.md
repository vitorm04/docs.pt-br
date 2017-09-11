---
title: "Habilitando a depuração por anexação JIT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
caps.latest.revision: 17
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5ca6d1e6ec5c19f690ab862b13783b9db05ac2a9
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="87a39-102">Habilitando a depuração por anexação JIT</span><span class="sxs-lookup"><span data-stu-id="87a39-102">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="87a39-103">A depuração de anexação JIT é a expressão usada para descrever a anexação de um depurador a um processo quando você encontra erros ou ela pode ser disparada por funções ou métodos específicos.</span><span class="sxs-lookup"><span data-stu-id="87a39-103">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="87a39-104">A depuração de anexação JIT é usada nas seguintes condições de falha:</span><span class="sxs-lookup"><span data-stu-id="87a39-104">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
-   <span data-ttu-id="87a39-105">Exceções sem tratamento (no código nativo e gerenciado).</span><span class="sxs-lookup"><span data-stu-id="87a39-105">Unhandled exceptions (in both native and managed code).</span></span>  
  
-   <span data-ttu-id="87a39-106">Método <xref:System.Environment.FailFast%2A?displayProperty=fullName> ou função [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) (família Windows 7).</span><span class="sxs-lookup"><span data-stu-id="87a39-106"><xref:System.Environment.FailFast%2A?displayProperty=fullName> method or [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) function (Windows 7 family).</span></span>  
  
-   <span data-ttu-id="87a39-107">Erros fatais de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="87a39-107">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="87a39-108">A depuração de anexação JIT também é disparada por chamadas às seguintes funções e métodos:</span><span class="sxs-lookup"><span data-stu-id="87a39-108">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
-   <span data-ttu-id="87a39-109">Método <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="87a39-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=fullName> method.</span></span>  
  
-   <span data-ttu-id="87a39-110">Método <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="87a39-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=fullName> method.</span></span>  
  
-   <span data-ttu-id="87a39-111">Função [DebugBreak](http://go.microsoft.com/fwlink/?LinkId=182106) (Win32).</span><span class="sxs-lookup"><span data-stu-id="87a39-111">[DebugBreak](http://go.microsoft.com/fwlink/?LinkId=182106) function (Win32).</span></span>  
  
 <span data-ttu-id="87a39-112">Antes do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], o .NET Framework fornecia chaves do Registro separadas para controlar o comportamento dos depuradores nativos e gerenciados.</span><span class="sxs-lookup"><span data-stu-id="87a39-112">Before the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="87a39-113">A partir do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], o controle é consolidado em uma única chave do Registro: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span><span class="sxs-lookup"><span data-stu-id="87a39-113">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="87a39-114">Os valores que podem ser definidos para essa chave determinam se um depurador é invocado e, nesse caso, se ele é invocado com uma caixa de diálogo que exige a interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="87a39-114">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="87a39-115">Para obter informações sobre como configurar essa chave do Registro, consulte [Configurando a depuração automática](http://go.microsoft.com/fwlink/?LinkId=181767) na Biblioteca MSDN.</span><span class="sxs-lookup"><span data-stu-id="87a39-115">For information about setting this registry key, see [Configuring Automatic Debugging](http://go.microsoft.com/fwlink/?LinkId=181767) in the MSDN Library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87a39-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87a39-116">See Also</span></span>  
 <span data-ttu-id="87a39-117">[Depuração, rastreamento e criação de perfil](../../../docs/framework/debug-trace-profile/index.md) </span><span class="sxs-lookup"><span data-stu-id="87a39-117">[Debugging, Tracing, and Profiling](../../../docs/framework/debug-trace-profile/index.md) </span></span>  
 <span data-ttu-id="87a39-118">[Facilitando a depuração de uma imagem](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md) </span><span class="sxs-lookup"><span data-stu-id="87a39-118">[Making an Image Easier to Debug](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md) </span></span>  
 [<span data-ttu-id="87a39-119">Habilitando a criação de perfil</span><span class="sxs-lookup"><span data-stu-id="87a39-119">Enabling Profiling</span></span>](http://msdn.microsoft.com/en-us/3b669676-f0e0-4ebf-8674-68986dd2020d)

