---
ms.openlocfilehash: cef8096c971da8ae245ff974697022f350cb9195
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616014"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="a1dba-101">VB.NET não é mais compatível com a qualificação do namespace parcial para APIs System.Windows</span><span class="sxs-lookup"><span data-stu-id="a1dba-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

#### <a name="details"></a><span data-ttu-id="a1dba-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="a1dba-102">Details</span></span>

<span data-ttu-id="a1dba-103">Começando com o .NET Framework 4.5.2, os projetos VB.NET não podem especificar APIs System.Windows com namespaces parcialmente qualificados.</span><span class="sxs-lookup"><span data-stu-id="a1dba-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="a1dba-104">Por exemplo, fazer referência a `Windows.Forms.DialogResult` falhará.</span><span class="sxs-lookup"><span data-stu-id="a1dba-104">For example, referring to `Windows.Forms.DialogResult` will fail.</span></span> <span data-ttu-id="a1dba-105">Em vez disso, o código deve fazer referência ao nome totalmente qualificado (<xref:System.Windows.Forms.DialogResult>) ou importar o namespace específico e simplesmente fazer referência a <xref:System.Windows.Forms.DialogResult?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="a1dba-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a1dba-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="a1dba-106">Suggestion</span></span>

<span data-ttu-id="a1dba-107">O código deve ser atualizado para fazer referência as APIs `System.Windows` com nomes simples (e importando o namespace relevante) ou com nomes totalmente qualificados.</span><span class="sxs-lookup"><span data-stu-id="a1dba-107">Code should be updated to refer to `System.Windows` APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>

| <span data-ttu-id="a1dba-108">Name</span><span class="sxs-lookup"><span data-stu-id="a1dba-108">Name</span></span>    | <span data-ttu-id="a1dba-109">Valor</span><span class="sxs-lookup"><span data-stu-id="a1dba-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a1dba-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="a1dba-110">Scope</span></span>   | <span data-ttu-id="a1dba-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="a1dba-111">Minor</span></span>       |
| <span data-ttu-id="a1dba-112">Versão</span><span class="sxs-lookup"><span data-stu-id="a1dba-112">Version</span></span> | <span data-ttu-id="a1dba-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="a1dba-113">4.5.2</span></span>       |
| <span data-ttu-id="a1dba-114">Type</span><span class="sxs-lookup"><span data-stu-id="a1dba-114">Type</span></span>    | <span data-ttu-id="a1dba-115">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="a1dba-115">Retargeting</span></span> |
