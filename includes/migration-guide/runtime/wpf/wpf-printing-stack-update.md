---
ms.openlocfilehash: 5e2e8d1ec5d698d1c1649c2a0a1b4b77dbdf4022
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621028"
---
### <a name="wpf-printing-stack-update"></a><span data-ttu-id="8b20e-101">Atualização da pilha de impressão do WPF</span><span class="sxs-lookup"><span data-stu-id="8b20e-101">WPF Printing Stack Update</span></span>

#### <a name="details"></a><span data-ttu-id="8b20e-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8b20e-102">Details</span></span>

<span data-ttu-id="8b20e-103">Agora, as APIs de Impressão do WPF que usam <xref:System.Printing.PrintQueue?displayProperty=fullName>chamam a API de Impressão Pacote de Documentos do Windows em vez da API de Impressão XPS, que foi preterida.</span><span class="sxs-lookup"><span data-stu-id="8b20e-103">WPF's Printing APIs using <xref:System.Printing.PrintQueue?displayProperty=fullName> now call Window's Print Document Package API in favor of the now deprecated XPS Print API.</span></span> <span data-ttu-id="8b20e-104">A alteração foi feita para fins de manutenção. Nem usuários nem os desenvolvedores devem ver todas as alterações no comportamento ou no uso da API.</span><span class="sxs-lookup"><span data-stu-id="8b20e-104">The change was made with serviceability in mind; neither users nor developers should see any changes in behavior or API usage.</span></span> <span data-ttu-id="8b20e-105">A nova pilha de impressão é habilitada por padrão ao ser executada na Atualização do Windows 10 para Criadores.</span><span class="sxs-lookup"><span data-stu-id="8b20e-105">The new printing stack is enabled by default when running in Windows 10 Creators Update.</span></span> <span data-ttu-id="8b20e-106">A pilha de impressão antiga continuará a funcionar como antes nas versões mais antigas do Windows.</span><span class="sxs-lookup"><span data-stu-id="8b20e-106">The old printing stack will still continue to work just as before in older Windows versions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8b20e-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="8b20e-107">Suggestion</span></span>

<span data-ttu-id="8b20e-108">Para usar a pilha antiga na Atualização do Windows 10 para Criadores, defina o valor REG_DWORD <code>UseXpsOMPrinting</code> da chave do Registro <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> como <code>1</code>.</span><span class="sxs-lookup"><span data-stu-id="8b20e-108">To use the old stack in Windows 10 Creators Update, set the <code>UseXpsOMPrinting</code> REG_DWORD value of the <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> registry key to <code>1</code>.</span></span>

| <span data-ttu-id="8b20e-109">Name</span><span class="sxs-lookup"><span data-stu-id="8b20e-109">Name</span></span>    | <span data-ttu-id="8b20e-110">Valor</span><span class="sxs-lookup"><span data-stu-id="8b20e-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8b20e-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="8b20e-111">Scope</span></span>   |<span data-ttu-id="8b20e-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="8b20e-112">Edge</span></span>|
|<span data-ttu-id="8b20e-113">Versão</span><span class="sxs-lookup"><span data-stu-id="8b20e-113">Version</span></span>|<span data-ttu-id="8b20e-114">4.7</span><span class="sxs-lookup"><span data-stu-id="8b20e-114">4.7</span></span>|
|<span data-ttu-id="8b20e-115">Type</span><span class="sxs-lookup"><span data-stu-id="8b20e-115">Type</span></span>|<span data-ttu-id="8b20e-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="8b20e-116">Runtime</span></span>|
