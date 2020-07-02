---
ms.openlocfilehash: 4ad7c4c2781480c08ad4cf27e40de445b1c50671
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617114"
---
### <a name="encoderparameter-ctor-is-obsolete"></a><span data-ttu-id="1b3e1-101">O construtor EncoderParameter está obsoleto</span><span class="sxs-lookup"><span data-stu-id="1b3e1-101">EncoderParameter ctor is obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="1b3e1-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1b3e1-102">Details</span></span>

<span data-ttu-id="1b3e1-103">O construtor <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> agora está obsoleto e introduzirá novos avisos de compilação se for usado.</span><span class="sxs-lookup"><span data-stu-id="1b3e1-103">The <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> constructor is obsolete now and will introduce build warnings if used.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1b3e1-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="1b3e1-104">Suggestion</span></span>

<span data-ttu-id="1b3e1-105">Embora o construtor <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> continue funcionando, o seguinte construtor deverá ser usado em seu lugar para evitar o aviso de build obsoleto durante a recompilação de código com as ferramentas do .NET Framework 4.5: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span><span class="sxs-lookup"><span data-stu-id="1b3e1-105">Although the <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>constructor will continue to work, the following constructor should be used instead to avoid the obsolete build warning when re-compiling code with .NET Framework  4.5 tools: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span></span>

| <span data-ttu-id="1b3e1-106">Name</span><span class="sxs-lookup"><span data-stu-id="1b3e1-106">Name</span></span>    | <span data-ttu-id="1b3e1-107">Valor</span><span class="sxs-lookup"><span data-stu-id="1b3e1-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1b3e1-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="1b3e1-108">Scope</span></span>   | <span data-ttu-id="1b3e1-109">Secundária</span><span class="sxs-lookup"><span data-stu-id="1b3e1-109">Minor</span></span>       |
| <span data-ttu-id="1b3e1-110">Versão</span><span class="sxs-lookup"><span data-stu-id="1b3e1-110">Version</span></span> | <span data-ttu-id="1b3e1-111">4.5</span><span class="sxs-lookup"><span data-stu-id="1b3e1-111">4.5</span></span>         |
| <span data-ttu-id="1b3e1-112">Type</span><span class="sxs-lookup"><span data-stu-id="1b3e1-112">Type</span></span>    | <span data-ttu-id="1b3e1-113">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="1b3e1-113">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="1b3e1-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1b3e1-114">Affected APIs</span></span>

- <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>
