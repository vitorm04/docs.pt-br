---
ms.openlocfilehash: 8db115a46df3fcea103e8fa6896542d0116aa256
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804665"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="17396-101">VB.NET não é mais compatível com a qualificação do namespace parcial para APIs System.Windows</span><span class="sxs-lookup"><span data-stu-id="17396-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

|   |   |
|---|---|
|<span data-ttu-id="17396-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="17396-102">Details</span></span>|<span data-ttu-id="17396-103">Começando com o .NET Framework 4.5.2, os projetos VB.NET não podem especificar APIs System.Windows com namespaces parcialmente qualificados.</span><span class="sxs-lookup"><span data-stu-id="17396-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="17396-104">Por exemplo, fazer referência a <code>Windows.Forms.DialogResult</code> falhará.</span><span class="sxs-lookup"><span data-stu-id="17396-104">For example, referring to <code>Windows.Forms.DialogResult</code> will fail.</span></span> <span data-ttu-id="17396-105">Em vez disso, o código deve fazer referência ao nome totalmente qualificado (<xref:System.Windows.Forms.DialogResult>) ou importar o namespace específico e simplesmente fazer referência a <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="17396-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span></span>|
|<span data-ttu-id="17396-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="17396-106">Suggestion</span></span>|<span data-ttu-id="17396-107">O código deve ser atualizado para fazer referência as APIs <code>System.Windows</code> com nomes simples (e importando o namespace relevante) ou com nomes totalmente qualificados.</span><span class="sxs-lookup"><span data-stu-id="17396-107">Code should be updated to refer to <code>System.Windows</code> APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>|
|<span data-ttu-id="17396-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="17396-108">Scope</span></span>|<span data-ttu-id="17396-109">Secundária</span><span class="sxs-lookup"><span data-stu-id="17396-109">Minor</span></span>|
|<span data-ttu-id="17396-110">Versão</span><span class="sxs-lookup"><span data-stu-id="17396-110">Version</span></span>|<span data-ttu-id="17396-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="17396-111">4.5.2</span></span>|
|<span data-ttu-id="17396-112">Type</span><span class="sxs-lookup"><span data-stu-id="17396-112">Type</span></span>|<span data-ttu-id="17396-113">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="17396-113">Retargeting</span></span>|
