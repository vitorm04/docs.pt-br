---
ms.openlocfilehash: 8db115a46df3fcea103e8fa6896542d0116aa256
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236719"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="f2d33-101">VB.NET não é mais compatível com a qualificação do namespace parcial para APIs System.Windows</span><span class="sxs-lookup"><span data-stu-id="f2d33-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f2d33-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f2d33-102">Details</span></span>|<span data-ttu-id="f2d33-103">Começando com o .NET Framework 4.5.2, os projetos VB.NET não podem especificar APIs System.Windows com namespaces parcialmente qualificados.</span><span class="sxs-lookup"><span data-stu-id="f2d33-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="f2d33-104">Por exemplo, fazer referência a <code>Windows.Forms.DialogResult</code> falhará.</span><span class="sxs-lookup"><span data-stu-id="f2d33-104">For example, referring to <code>Windows.Forms.DialogResult</code> will fail.</span></span> <span data-ttu-id="f2d33-105">Em vez disso, o código deve fazer referência ao nome totalmente qualificado (<xref:System.Windows.Forms.DialogResult>) ou importar o namespace específico e simplesmente fazer referência a <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="f2d33-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span></span>|
|<span data-ttu-id="f2d33-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="f2d33-106">Suggestion</span></span>|<span data-ttu-id="f2d33-107">O código deve ser atualizado para fazer referência as APIs <code>System.Windows</code> com nomes simples (e importando o namespace relevante) ou com nomes totalmente qualificados.</span><span class="sxs-lookup"><span data-stu-id="f2d33-107">Code should be updated to refer to <code>System.Windows</code> APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>|
|<span data-ttu-id="f2d33-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="f2d33-108">Scope</span></span>|<span data-ttu-id="f2d33-109">Secundário</span><span class="sxs-lookup"><span data-stu-id="f2d33-109">Minor</span></span>|
|<span data-ttu-id="f2d33-110">Versão</span><span class="sxs-lookup"><span data-stu-id="f2d33-110">Version</span></span>|<span data-ttu-id="f2d33-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="f2d33-111">4.5.2</span></span>|
|<span data-ttu-id="f2d33-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="f2d33-112">Type</span></span>|<span data-ttu-id="f2d33-113">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="f2d33-113">Retargeting</span></span>|
