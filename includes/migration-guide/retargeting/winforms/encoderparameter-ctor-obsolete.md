---
ms.openlocfilehash: b4e062fe3a00b76da144e706841f87b2a95888e5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774281"
---
### <a name="encoderparameter-ctor-is-obsolete"></a><span data-ttu-id="ecd1b-101">O construtor EncoderParameter está obsoleto</span><span class="sxs-lookup"><span data-stu-id="ecd1b-101">EncoderParameter ctor is obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ecd1b-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ecd1b-102">Details</span></span>|<span data-ttu-id="ecd1b-103">O construtor <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> agora está obsoleto e introduzirá novos avisos de compilação se for usado.</span><span class="sxs-lookup"><span data-stu-id="ecd1b-103">The <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> constructor is obsolete now and will introduce build warnings if used.</span></span>|
|<span data-ttu-id="ecd1b-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="ecd1b-104">Suggestion</span></span>|<span data-ttu-id="ecd1b-105">Embora o construtor <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> continue funcionando, o seguinte construtor deverá ser usado em seu lugar para evitar o aviso de build obsoleto durante a recompilação de código com as ferramentas do .NET Framework 4.5: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span><span class="sxs-lookup"><span data-stu-id="ecd1b-105">Although the <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>constructor will continue to work, the following constructor should be used instead to avoid the obsolete build warning when re-compiling code with .NET Framework  4.5 tools: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span></span>|
|<span data-ttu-id="ecd1b-106">Escopo</span><span class="sxs-lookup"><span data-stu-id="ecd1b-106">Scope</span></span>|<span data-ttu-id="ecd1b-107">Secundário</span><span class="sxs-lookup"><span data-stu-id="ecd1b-107">Minor</span></span>|
|<span data-ttu-id="ecd1b-108">Versão</span><span class="sxs-lookup"><span data-stu-id="ecd1b-108">Version</span></span>|<span data-ttu-id="ecd1b-109">4.5</span><span class="sxs-lookup"><span data-stu-id="ecd1b-109">4.5</span></span>|
|<span data-ttu-id="ecd1b-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="ecd1b-110">Type</span></span>|<span data-ttu-id="ecd1b-111">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="ecd1b-111">Retargeting</span></span>|
|<span data-ttu-id="ecd1b-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ecd1b-112">Affected APIs</span></span>|<ul><li><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
