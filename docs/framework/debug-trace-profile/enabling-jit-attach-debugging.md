---
title: Habilitando a depuração por anexação JIT
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67db256f4c328b12d6cc30abfbe5d5ccc12e8b0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397826"
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="e15da-102">Habilitando a depuração por anexação JIT</span><span class="sxs-lookup"><span data-stu-id="e15da-102">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="e15da-103">A depuração de anexação JIT é a expressão usada para descrever a anexação de um depurador a um processo quando você encontra erros ou ela pode ser disparada por funções ou métodos específicos.</span><span class="sxs-lookup"><span data-stu-id="e15da-103">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="e15da-104">A depuração de anexação JIT é usada nas seguintes condições de falha:</span><span class="sxs-lookup"><span data-stu-id="e15da-104">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
-   <span data-ttu-id="e15da-105">Exceções sem tratamento (no código nativo e gerenciado).</span><span class="sxs-lookup"><span data-stu-id="e15da-105">Unhandled exceptions (in both native and managed code).</span></span>  
  
-   <span data-ttu-id="e15da-106">Método <xref:System.Environment.FailFast%2A?displayProperty=nameWithType> ou função [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) (família Windows 7).</span><span class="sxs-lookup"><span data-stu-id="e15da-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) function (Windows 7 family).</span></span>  
  
-   <span data-ttu-id="e15da-107">Erros fatais de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e15da-107">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="e15da-108">A depuração de anexação JIT também é disparada por chamadas às seguintes funções e métodos:</span><span class="sxs-lookup"><span data-stu-id="e15da-108">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
-   <span data-ttu-id="e15da-109">Método <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e15da-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="e15da-110">Método <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e15da-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="e15da-111">Função [DebugBreak](http://go.microsoft.com/fwlink/?LinkId=182106) (Win32).</span><span class="sxs-lookup"><span data-stu-id="e15da-111">[DebugBreak](http://go.microsoft.com/fwlink/?LinkId=182106) function (Win32).</span></span>  
  
 <span data-ttu-id="e15da-112">Antes do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], o .NET Framework fornecia chaves do Registro separadas para controlar o comportamento dos depuradores nativos e gerenciados.</span><span class="sxs-lookup"><span data-stu-id="e15da-112">Before the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="e15da-113">A partir do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], o controle é consolidado em uma única chave do Registro: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span><span class="sxs-lookup"><span data-stu-id="e15da-113">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="e15da-114">Os valores que podem ser definidos para essa chave determinam se um depurador é invocado e, nesse caso, se ele é invocado com uma caixa de diálogo que exige a interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="e15da-114">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="e15da-115">Para obter informações sobre como configurar essa chave do registro, consulte [Configurando depuração automática](http://go.microsoft.com/fwlink/?LinkId=181767).</span><span class="sxs-lookup"><span data-stu-id="e15da-115">For information about setting this registry key, see [Configuring Automatic Debugging](http://go.microsoft.com/fwlink/?LinkId=181767).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e15da-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e15da-116">See Also</span></span>  
 [<span data-ttu-id="e15da-117">Depuração, rastreamento e criação de perfil</span><span class="sxs-lookup"><span data-stu-id="e15da-117">Debugging, Tracing, and Profiling</span></span>](../../../docs/framework/debug-trace-profile/index.md)  
 [<span data-ttu-id="e15da-118">Facilitando a depuração de uma imagem</span><span class="sxs-lookup"><span data-stu-id="e15da-118">Making an Image Easier to Debug</span></span>](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 [<span data-ttu-id="e15da-119">Habilitando a criação de perfil</span><span class="sxs-lookup"><span data-stu-id="e15da-119">Enabling Profiling</span></span>](http://msdn.microsoft.com/library/3b669676-f0e0-4ebf-8674-68986dd2020d)
