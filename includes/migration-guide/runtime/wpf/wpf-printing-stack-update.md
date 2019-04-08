---
ms.openlocfilehash: e613f0c52c77efebf250f5935d5cbfc29bc09a6b
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760399"
---
### <a name="wpf-printing-stack-update"></a><span data-ttu-id="5e6c4-101">Atualização da pilha de impressão do WPF</span><span class="sxs-lookup"><span data-stu-id="5e6c4-101">WPF Printing Stack Update</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5e6c4-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="5e6c4-102">Details</span></span>|<span data-ttu-id="5e6c4-103">Agora, as APIs de Impressão do WPF que usam <xref:System.Printing.PrintQueue?displayProperty=name>chamam a API de Impressão Pacote de Documentos do Windows em vez da API de Impressão XPS, que foi preterida.</span><span class="sxs-lookup"><span data-stu-id="5e6c4-103">WPF's Printing APIs using <xref:System.Printing.PrintQueue?displayProperty=name> now call Window's Print Document Package API in favor of the now deprecated XPS Print API.</span></span> <span data-ttu-id="5e6c4-104">A alteração foi feita para fins de manutenção. Nem usuários nem os desenvolvedores devem ver todas as alterações no comportamento ou no uso da API.</span><span class="sxs-lookup"><span data-stu-id="5e6c4-104">The change was made with serviceability in mind; neither users nor developers should see any changes in behavior or API usage.</span></span> <span data-ttu-id="5e6c4-105">A nova pilha de impressão é habilitada por padrão ao ser executada na Atualização do Windows 10 para Criadores.</span><span class="sxs-lookup"><span data-stu-id="5e6c4-105">The new printing stack is enabled by default when running in Windows 10 Creators Update.</span></span> <span data-ttu-id="5e6c4-106">A pilha de impressão antiga continuará a funcionar como antes nas versões mais antigas do Windows.</span><span class="sxs-lookup"><span data-stu-id="5e6c4-106">The old printing stack will still continue to work just as before in older Windows versions.</span></span>|
|<span data-ttu-id="5e6c4-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="5e6c4-107">Suggestion</span></span>|<span data-ttu-id="5e6c4-108">Para usar a pilha antiga na Atualização do Windows 10 para Criadores, defina o valor REG_DWORD <code>UseXpsOMPrinting</code> da chave do Registro <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> como <code>1</code>.</span><span class="sxs-lookup"><span data-stu-id="5e6c4-108">To use the old stack in Windows 10 Creators Update, set the <code>UseXpsOMPrinting</code> REG_DWORD value of the <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> registry key to <code>1</code>.</span></span>|
|<span data-ttu-id="5e6c4-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="5e6c4-109">Scope</span></span>|<span data-ttu-id="5e6c4-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="5e6c4-110">Edge</span></span>|
|<span data-ttu-id="5e6c4-111">Versão</span><span class="sxs-lookup"><span data-stu-id="5e6c4-111">Version</span></span>|<span data-ttu-id="5e6c4-112">4.7</span><span class="sxs-lookup"><span data-stu-id="5e6c4-112">4.7</span></span>|
|<span data-ttu-id="5e6c4-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="5e6c4-113">Type</span></span>|<span data-ttu-id="5e6c4-114">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5e6c4-114">Runtime</span></span>|

