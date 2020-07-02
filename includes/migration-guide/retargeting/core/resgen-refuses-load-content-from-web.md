---
ms.openlocfilehash: f980c8029375074889505a8eb7e8a65aaa8d74e4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614292"
---
### <a name="resgen-refuses-to-load-content-from-the-web"></a><span data-ttu-id="27914-101">O Resgen recusa a carregar conteúdo da Web</span><span class="sxs-lookup"><span data-stu-id="27914-101">Resgen refuses to load content from the web</span></span>

#### <a name="details"></a><span data-ttu-id="27914-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="27914-102">Details</span></span>

<span data-ttu-id="27914-103">arquivos. resx podem conter entrada binária formatada.</span><span class="sxs-lookup"><span data-stu-id="27914-103">.resx files may contain binary formatted input.</span></span> <span data-ttu-id="27914-104">Se você tentar usar Resgen para carregar um arquivo que foi baixado de um local não confiável, ele falhará ao carregar a entrada por padrão.</span><span class="sxs-lookup"><span data-stu-id="27914-104">If you attempt to use resgen to load a file that was downloaded from an untrusted location, it will fail to load the input by default.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="27914-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="27914-105">Suggestion</span></span>

<span data-ttu-id="27914-106">Os usuários ResGen que exigem o carregamento de entradas formatadas binárias de locais não confiáveis podem remover a marca da Web do arquivo de entrada ou aplicar a sutileza da recusa. Adicione a seguinte configuração do registro para aplicar a peculiarização de aceitação por todo o computador: [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft.netframework\sdk] &quot; AllowProcessOfUntrustedResourceFiles &quot; = &quot; true&quot;</span><span class="sxs-lookup"><span data-stu-id="27914-106">Resgen users who require loading binary formatted input from untrusted locations can either remove the mark of the web from the input file or apply the opt-out quirk.Add the following registry setting to apply the machine wide opt-out quirk: [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework\SDK] &quot;AllowProcessOfUntrustedResourceFiles&quot;=&quot;true&quot;</span></span>

| <span data-ttu-id="27914-107">Name</span><span class="sxs-lookup"><span data-stu-id="27914-107">Name</span></span>    | <span data-ttu-id="27914-108">Valor</span><span class="sxs-lookup"><span data-stu-id="27914-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="27914-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="27914-109">Scope</span></span>   | <span data-ttu-id="27914-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="27914-110">Edge</span></span>        |
| <span data-ttu-id="27914-111">Versão</span><span class="sxs-lookup"><span data-stu-id="27914-111">Version</span></span> | <span data-ttu-id="27914-112">4.7.2</span><span class="sxs-lookup"><span data-stu-id="27914-112">4.7.2</span></span>       |
| <span data-ttu-id="27914-113">Type</span><span class="sxs-lookup"><span data-stu-id="27914-113">Type</span></span>    | <span data-ttu-id="27914-114">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="27914-114">Retargeting</span></span> |
