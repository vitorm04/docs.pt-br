---
title: Habilitando a depuração por anexação JIT
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4d4e2b3806d2c4d84b59e1cd44eb03ab7b278c9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052834"
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="caa60-102">Habilitando a depuração por anexação JIT</span><span class="sxs-lookup"><span data-stu-id="caa60-102">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="caa60-103">A depuração de anexação JIT é a expressão usada para descrever a anexação de um depurador a um processo quando você encontra erros ou ela pode ser disparada por funções ou métodos específicos.</span><span class="sxs-lookup"><span data-stu-id="caa60-103">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="caa60-104">A depuração de anexação JIT é usada nas seguintes condições de falha:</span><span class="sxs-lookup"><span data-stu-id="caa60-104">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
- <span data-ttu-id="caa60-105">Exceções sem tratamento (no código nativo e gerenciado).</span><span class="sxs-lookup"><span data-stu-id="caa60-105">Unhandled exceptions (in both native and managed code).</span></span>  
  
- <span data-ttu-id="caa60-106">Método <xref:System.Environment.FailFast%2A?displayProperty=nameWithType> ou função [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) (família Windows 7).</span><span class="sxs-lookup"><span data-stu-id="caa60-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) function (Windows 7 family).</span></span>  
  
- <span data-ttu-id="caa60-107">Erros fatais de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="caa60-107">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="caa60-108">A depuração de anexação JIT também é disparada por chamadas às seguintes funções e métodos:</span><span class="sxs-lookup"><span data-stu-id="caa60-108">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
- <span data-ttu-id="caa60-109">Método <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="caa60-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="caa60-110">Método <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="caa60-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="caa60-111">Função [DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) (Win32).</span><span class="sxs-lookup"><span data-stu-id="caa60-111">[DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) function (Win32).</span></span>  
  
 <span data-ttu-id="caa60-112">Antes do .NET Framework 4, o .NET Framework forneceu chaves de registro separadas para controlar o comportamento de depuradores nativos e gerenciados.</span><span class="sxs-lookup"><span data-stu-id="caa60-112">Before the .NET Framework 4, the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="caa60-113">A partir do .NET Framework 4, o controle é consolidado em uma única chave do registro: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span><span class="sxs-lookup"><span data-stu-id="caa60-113">Starting with the .NET Framework 4, control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="caa60-114">Os valores que podem ser definidos para essa chave determinam se um depurador é invocado e, nesse caso, se ele é invocado com uma caixa de diálogo que exige a interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="caa60-114">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="caa60-115">Para obter informações sobre como definir essa chave do registro, consulte [Configurando a depuração automática](https://go.microsoft.com/fwlink/?LinkId=181767).</span><span class="sxs-lookup"><span data-stu-id="caa60-115">For information about setting this registry key, see [Configuring Automatic Debugging](https://go.microsoft.com/fwlink/?LinkId=181767).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caa60-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="caa60-116">See also</span></span>

- [<span data-ttu-id="caa60-117">Depuração, rastreamento e criação de perfil</span><span class="sxs-lookup"><span data-stu-id="caa60-117">Debugging, Tracing, and Profiling</span></span>](index.md)
- [<span data-ttu-id="caa60-118">Facilitando a depuração de uma imagem</span><span class="sxs-lookup"><span data-stu-id="caa60-118">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)
