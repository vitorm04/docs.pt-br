---
title: Habilitando a depuração por anexação JIT
description: Habilite a depuração de anexação JIT (just-in-time) para anexar um depurador a um processo quando você encontrar erros. Ele pode ser disparado por determinados métodos ou funções.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
ms.openlocfilehash: d1190c51a9cc6b5322ec832e0d35bc01dc855b12
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416038"
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="050b9-104">Habilitando a depuração por anexação JIT</span><span class="sxs-lookup"><span data-stu-id="050b9-104">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="050b9-105">A depuração de anexação JIT é a expressão usada para descrever a anexação de um depurador a um processo quando você encontra erros ou ela pode ser disparada por funções ou métodos específicos.</span><span class="sxs-lookup"><span data-stu-id="050b9-105">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="050b9-106">A depuração de anexação JIT é usada nas seguintes condições de falha:</span><span class="sxs-lookup"><span data-stu-id="050b9-106">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
- <span data-ttu-id="050b9-107">Exceções sem tratamento (no código nativo e gerenciado).</span><span class="sxs-lookup"><span data-stu-id="050b9-107">Unhandled exceptions (in both native and managed code).</span></span>  
  
- <span data-ttu-id="050b9-108">Método <xref:System.Environment.FailFast%2A?displayProperty=nameWithType> ou função [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) (família Windows 7).</span><span class="sxs-lookup"><span data-stu-id="050b9-108"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) function (Windows 7 family).</span></span>  
  
- <span data-ttu-id="050b9-109">Erros fatais de runtime.</span><span class="sxs-lookup"><span data-stu-id="050b9-109">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="050b9-110">A depuração de anexação JIT também é disparada por chamadas às seguintes funções e métodos:</span><span class="sxs-lookup"><span data-stu-id="050b9-110">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
- <span data-ttu-id="050b9-111">Método <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="050b9-111"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="050b9-112">Método <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="050b9-112"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="050b9-113">Função [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) (Win32).</span><span class="sxs-lookup"><span data-stu-id="050b9-113">[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) function (Win32).</span></span>  
  
 <span data-ttu-id="050b9-114">Antes do .NET Framework 4, o .NET Framework forneceu chaves de registro separadas para controlar o comportamento de depuradores nativos e gerenciados.</span><span class="sxs-lookup"><span data-stu-id="050b9-114">Before the .NET Framework 4, the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="050b9-115">A partir do .NET Framework 4, o controle é consolidado em uma única chave do registro: HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span><span class="sxs-lookup"><span data-stu-id="050b9-115">Starting with the .NET Framework 4, control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="050b9-116">Os valores que podem ser definidos para essa chave determinam se um depurador é invocado e, nesse caso, se ele é invocado com uma caixa de diálogo que exige a interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="050b9-116">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="050b9-117">Para obter informações sobre como definir essa chave do registro, consulte [Configurando a depuração automática](/windows/win32/debug/configuring-automatic-debugging).</span><span class="sxs-lookup"><span data-stu-id="050b9-117">For information about setting this registry key, see [Configuring Automatic Debugging](/windows/win32/debug/configuring-automatic-debugging).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="050b9-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="050b9-118">See also</span></span>

- [<span data-ttu-id="050b9-119">Depuração, rastreamento e criação de perfil</span><span class="sxs-lookup"><span data-stu-id="050b9-119">Debugging, Tracing, and Profiling</span></span>](index.md)
- [<span data-ttu-id="050b9-120">Facilitar a depuração de uma imagem</span><span class="sxs-lookup"><span data-stu-id="050b9-120">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)
