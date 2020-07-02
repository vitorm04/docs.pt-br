---
ms.openlocfilehash: f907cb1939e111c586d68243e6b8a8e291974e36
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615599"
---
### <a name="wpf-layout-rounding-of-margins-has-changed"></a><span data-ttu-id="8e218-101">Arredondamento de layout do WPF foi alterado</span><span class="sxs-lookup"><span data-stu-id="8e218-101">WPF layout rounding of margins has changed</span></span>

#### <a name="details"></a><span data-ttu-id="8e218-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8e218-102">Details</span></span>

<span data-ttu-id="8e218-103">A maneira como as margens são arredondadas, bem como as bordas e a tela de fundo dentro delas, foi alterada.</span><span class="sxs-lookup"><span data-stu-id="8e218-103">The way in which margins are rounded and borders and the background inside of them has changed.</span></span> <span data-ttu-id="8e218-104">Como resultado dessa alteração:</span><span class="sxs-lookup"><span data-stu-id="8e218-104">As a result of this change:</span></span>

- <span data-ttu-id="8e218-105">A largura ou altura dos elementos pode aumentar ou reduzir em um pixel no máximo.</span><span class="sxs-lookup"><span data-stu-id="8e218-105">The width or height of elements may grow or shrink by at most one pixel.</span></span>
- <span data-ttu-id="8e218-106">O posicionamento de um objeto pode ser movido até um pixel, no máximo.</span><span class="sxs-lookup"><span data-stu-id="8e218-106">The placement of an object can move by at most one pixel.</span></span>
- <span data-ttu-id="8e218-107">Os elementos centralizados podem estar vertical ou horizontalmente fora do centro em, no máximo, um pixel.</span><span class="sxs-lookup"><span data-stu-id="8e218-107">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>
<span data-ttu-id="8e218-108">Por padrão, esse novo layout é habilitado somente para aplicativos que se destinam ao .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="8e218-108">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8e218-109">Sugestão</span><span class="sxs-lookup"><span data-stu-id="8e218-109">Suggestion</span></span>

<span data-ttu-id="8e218-110">Uma vez que essa modificação tende a eliminar a distorção da direita ou da parte inferior dos controles do WPF em DPIs altos, os aplicativos que de destinam a versões anteriores do .NET Framework, mas estão sendo executados no .NET Framework 4.6, podem aderir a esse novo comportamento adicionando a seguinte linha à seção `<runtime>` do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="8e218-110">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>

<span data-ttu-id="8e218-111">Os aplicativos que são direcionados ao .NET Framework 4.6, mas querem que os controles do WPF sejam renderizados usando o algoritmo de layout anterior podem fazer isso adicionando a seguinte linha à seção `<runtime>` do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="8e218-111">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the `<runtime>` section of the app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>

| <span data-ttu-id="8e218-112">Name</span><span class="sxs-lookup"><span data-stu-id="8e218-112">Name</span></span>    | <span data-ttu-id="8e218-113">Valor</span><span class="sxs-lookup"><span data-stu-id="8e218-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8e218-114">Escopo</span><span class="sxs-lookup"><span data-stu-id="8e218-114">Scope</span></span>   | <span data-ttu-id="8e218-115">Secundária</span><span class="sxs-lookup"><span data-stu-id="8e218-115">Minor</span></span>       |
| <span data-ttu-id="8e218-116">Versão</span><span class="sxs-lookup"><span data-stu-id="8e218-116">Version</span></span> | <span data-ttu-id="8e218-117">4.6</span><span class="sxs-lookup"><span data-stu-id="8e218-117">4.6</span></span>         |
| <span data-ttu-id="8e218-118">Type</span><span class="sxs-lookup"><span data-stu-id="8e218-118">Type</span></span>    | <span data-ttu-id="8e218-119">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="8e218-119">Retargeting</span></span> |
