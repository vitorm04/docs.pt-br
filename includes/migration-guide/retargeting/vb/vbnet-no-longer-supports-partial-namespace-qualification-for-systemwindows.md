---
ms.openlocfilehash: 43e9c1c2f03daedf4d56152da5672b89399a3c69
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804665"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="e9e21-101">VB.NET não é mais compatível com a qualificação do namespace parcial para APIs System.Windows</span><span class="sxs-lookup"><span data-stu-id="e9e21-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e9e21-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e9e21-102">Details</span></span>|<span data-ttu-id="e9e21-103">Começando com o .NET Framework 4.5.2, os projetos VB.NET não podem especificar APIs System.Windows com namespaces parcialmente qualificados.</span><span class="sxs-lookup"><span data-stu-id="e9e21-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="e9e21-104">Por exemplo, fazer referência a <code>Windows.Forms.DialogResult</code> falhará.</span><span class="sxs-lookup"><span data-stu-id="e9e21-104">For example, referring to <code>Windows.Forms.DialogResult</code> will fail.</span></span> <span data-ttu-id="e9e21-105">Em vez disso, o código deve fazer referência ao nome totalmente qualificado (<xref:System.Windows.Forms.DialogResult>) ou importar o namespace específico e simplesmente fazer referência a <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="e9e21-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span></span>|
|<span data-ttu-id="e9e21-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e9e21-106">Suggestion</span></span>|<span data-ttu-id="e9e21-107">O código deve ser atualizado para fazer referência as APIs <code>System.Windows</code> com nomes simples (e importando o namespace relevante) ou com nomes totalmente qualificados.</span><span class="sxs-lookup"><span data-stu-id="e9e21-107">Code should be updated to refer to <code>System.Windows</code> APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>|
|<span data-ttu-id="e9e21-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="e9e21-108">Scope</span></span>|<span data-ttu-id="e9e21-109">Secundário</span><span class="sxs-lookup"><span data-stu-id="e9e21-109">Minor</span></span>|
|<span data-ttu-id="e9e21-110">Versão</span><span class="sxs-lookup"><span data-stu-id="e9e21-110">Version</span></span>|<span data-ttu-id="e9e21-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="e9e21-111">4.5.2</span></span>|
|<span data-ttu-id="e9e21-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="e9e21-112">Type</span></span>|<span data-ttu-id="e9e21-113">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="e9e21-113">Retargeting</span></span>|

