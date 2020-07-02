---
ms.openlocfilehash: e66a5c2a33a4ab5cf35013c1843936ffd01f90a2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614288"
---
### <a name="serialport-background-thread-exceptions"></a><span data-ttu-id="3ebe1-101">Exceções de thread de tela de fundo de SerialPort</span><span class="sxs-lookup"><span data-stu-id="3ebe1-101">SerialPort background thread exceptions</span></span>

#### <a name="details"></a><span data-ttu-id="3ebe1-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="3ebe1-102">Details</span></span>

<span data-ttu-id="3ebe1-103">Threads em segundo plano criados com fluxos <xref:System.IO.Ports.SerialPort> não terminam o processo quando são geradas exceções do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="3ebe1-103">Background threads created with <xref:System.IO.Ports.SerialPort> streams no longer terminate the process when OS exceptions are thrown.</span></span> <br/><span data-ttu-id="3ebe1-104">Em aplicativos direcionados ao .NET Framework 4.7 e a versões anteriores, um processo é terminado quando uma exceção do sistema operacional é gerada em um thread em segundo plano criado com um fluxo <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="3ebe1-104">In applications that target the .NET Framework 4.7 and earlier versions, a process is terminated when an operating system exception is thrown on a background thread created with a <xref:System.IO.Ports.SerialPort> stream.</span></span> <br/><span data-ttu-id="3ebe1-105">Nos aplicativos direcionados ao .NET Framework 4.7.1 e a versões anteriores, os threads em segundo plano esperam pelos eventos do SO relacionados à porta serial ativa e podem falhar em alguns casos, como uma remoção repentina da porta serial.</span><span class="sxs-lookup"><span data-stu-id="3ebe1-105">In applications that target the .NET Framework 4.7.1 or a later version, background threads wait for OS events related to the active serial port and could crash in some cases, such as sudden removal of the serial port.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3ebe1-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="3ebe1-106">Suggestion</span></span>

<span data-ttu-id="3ebe1-107">Para aplicativos destinados ao .NET Framework 4.7.1, será possível recusar a manipulação de exceções se ela não for desejável adicionando o seguinte à seção `<runtime>` do arquivo `app.config`:</span><span class="sxs-lookup"><span data-stu-id="3ebe1-107">For apps that target the .NET Framework 4.7.1, you can opt out of the exception handling if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true" />
</runtime>
```

<span data-ttu-id="3ebe1-108">Para aplicativos destinados a versões anteriores do .NET Framework mas executados no .NET Framework 4.7.1 ou posterior, é possível aceitar a manipulação de exceções adicionando o seguinte à seção `<runtime>` do arquivo `app.config`:</span><span class="sxs-lookup"><span data-stu-id="3ebe1-108">For apps that target earlier versions of the .NET Framework but run on the .NET Framework 4.7.1 or later, you can opt in to the exception handling by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false" />
</runtime>
```

| <span data-ttu-id="3ebe1-109">Name</span><span class="sxs-lookup"><span data-stu-id="3ebe1-109">Name</span></span>    | <span data-ttu-id="3ebe1-110">Valor</span><span class="sxs-lookup"><span data-stu-id="3ebe1-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3ebe1-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="3ebe1-111">Scope</span></span>   | <span data-ttu-id="3ebe1-112">Secundária</span><span class="sxs-lookup"><span data-stu-id="3ebe1-112">Minor</span></span>       |
| <span data-ttu-id="3ebe1-113">Versão</span><span class="sxs-lookup"><span data-stu-id="3ebe1-113">Version</span></span> | <span data-ttu-id="3ebe1-114">4.7.1</span><span class="sxs-lookup"><span data-stu-id="3ebe1-114">4.7.1</span></span>       |
| <span data-ttu-id="3ebe1-115">Type</span><span class="sxs-lookup"><span data-stu-id="3ebe1-115">Type</span></span>    | <span data-ttu-id="3ebe1-116">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="3ebe1-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="3ebe1-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="3ebe1-117">Affected APIs</span></span>

- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
