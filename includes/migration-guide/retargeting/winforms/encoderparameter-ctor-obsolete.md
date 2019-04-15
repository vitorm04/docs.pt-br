---
ms.openlocfilehash: b4e062fe3a00b76da144e706841f87b2a95888e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234593"
---
### <a name="encoderparameter-ctor-is-obsolete"></a><span data-ttu-id="50518-101">O construtor EncoderParameter está obsoleto</span><span class="sxs-lookup"><span data-stu-id="50518-101">EncoderParameter ctor is obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="50518-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="50518-102">Details</span></span>|<span data-ttu-id="50518-103">O construtor <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> agora está obsoleto e introduzirá novos avisos de compilação se for usado.</span><span class="sxs-lookup"><span data-stu-id="50518-103">The <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> constructor is obsolete now and will introduce build warnings if used.</span></span>|
|<span data-ttu-id="50518-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="50518-104">Suggestion</span></span>|<span data-ttu-id="50518-105">Embora o construtor <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> continue funcionando, o seguinte construtor deverá ser usado em seu lugar para evitar o aviso de build obsoleto durante a recompilação de código com as ferramentas do .NET Framework 4.5: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span><span class="sxs-lookup"><span data-stu-id="50518-105">Although the <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>constructor will continue to work, the following constructor should be used instead to avoid the obsolete build warning when re-compiling code with .NET Framework  4.5 tools: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span></span>|
|<span data-ttu-id="50518-106">Escopo</span><span class="sxs-lookup"><span data-stu-id="50518-106">Scope</span></span>|<span data-ttu-id="50518-107">Secundário</span><span class="sxs-lookup"><span data-stu-id="50518-107">Minor</span></span>|
|<span data-ttu-id="50518-108">Versão</span><span class="sxs-lookup"><span data-stu-id="50518-108">Version</span></span>|<span data-ttu-id="50518-109">4.5</span><span class="sxs-lookup"><span data-stu-id="50518-109">4.5</span></span>|
|<span data-ttu-id="50518-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="50518-110">Type</span></span>|<span data-ttu-id="50518-111">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="50518-111">Retargeting</span></span>|
|<span data-ttu-id="50518-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="50518-112">Affected APIs</span></span>|<ul><li><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
