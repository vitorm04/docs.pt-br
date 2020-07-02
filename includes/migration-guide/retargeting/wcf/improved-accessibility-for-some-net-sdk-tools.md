---
ms.openlocfilehash: f78d15338aa49de5b729aca12964924a0df00ec6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614301"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a><span data-ttu-id="c3b23-101">Acessibilidade aprimorada para algumas ferramentas do SDK do .NET</span><span class="sxs-lookup"><span data-stu-id="c3b23-101">Improved accessibility for some .NET SDK tools</span></span>

#### <a name="details"></a><span data-ttu-id="c3b23-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c3b23-102">Details</span></span>

<span data-ttu-id="c3b23-103">No SDK do .NET Framework 4.7.1, as ferramentas SvcConfigEditor.exe e SvcTraceViewer.exe foram melhoradas com a correção de vários problemas de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="c3b23-103">In the .NET Framework SDK 4.7.1, the SvcConfigEditor.exe and SvcTraceViewer.exe tools have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="c3b23-104">A maioria eram problemas pequenos como um nome que não está definido ou certos padrões de automação de interface do usuário implementados incorretamente.</span><span class="sxs-lookup"><span data-stu-id="c3b23-104">Most of these were small issues like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="c3b23-105">Embora muitos usuários não saibam esses valores incorretos, os clientes que usam tecnologias assistenciais como leitores de tela acharão essas ferramentas de SDK mais acessíveis.</span><span class="sxs-lookup"><span data-stu-id="c3b23-105">While many users wouldn't be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span> <span data-ttu-id="c3b23-106">Certamente, essas correções alteram alguns comportamentos anteriores, como a ordem do foco do teclado. Para obter todas as correções de acessibilidade nessas ferramentas, é possível adicionar o seguinte ao arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="c3b23-106">Certainly, these fixes change some previous behaviors, like keyboard focus order.In order to get all the accessibility fixes in these tools, you can the following to your app.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false"/>
</runtime>
```

| <span data-ttu-id="c3b23-107">Name</span><span class="sxs-lookup"><span data-stu-id="c3b23-107">Name</span></span>    | <span data-ttu-id="c3b23-108">Valor</span><span class="sxs-lookup"><span data-stu-id="c3b23-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c3b23-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="c3b23-109">Scope</span></span>   | <span data-ttu-id="c3b23-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="c3b23-110">Edge</span></span>        |
| <span data-ttu-id="c3b23-111">Versão</span><span class="sxs-lookup"><span data-stu-id="c3b23-111">Version</span></span> | <span data-ttu-id="c3b23-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="c3b23-112">4.7.1</span></span>       |
| <span data-ttu-id="c3b23-113">Type</span><span class="sxs-lookup"><span data-stu-id="c3b23-113">Type</span></span>    | <span data-ttu-id="c3b23-114">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="c3b23-114">Retargeting</span></span> |
