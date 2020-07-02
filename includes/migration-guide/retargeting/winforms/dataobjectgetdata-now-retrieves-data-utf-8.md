---
ms.openlocfilehash: 3f330d5e601d599231ef0336b785e677fe1d114e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616015"
---
### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a><span data-ttu-id="ed433-101">DataObject.GetData agora recupera dados como UTF-8</span><span class="sxs-lookup"><span data-stu-id="ed433-101">DataObject.GetData now retrieves data as UTF-8</span></span>

#### <a name="details"></a><span data-ttu-id="ed433-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ed433-102">Details</span></span>

<span data-ttu-id="ed433-103">Para aplicativos destinados ao .NET Framework 4 ou que são executados no .NET Framework 4.5.1 ou em versões mais recentes, `DataObject.GetData` recupera dados formatados em HTML como uma cadeia de caracteres ASCII.</span><span class="sxs-lookup"><span data-stu-id="ed433-103">For apps that target the .NET Framework 4 or that run on the .NET Framework 4.5.1 or earlier versions, `DataObject.GetData` retrieves HTML-formatted data as an ASCII string.</span></span> <span data-ttu-id="ed433-104">Como resultado, caracteres não ASCII (caracteres cujos códigos ASCII são maiores que 0x7F) são representados por dois caracteres aleatórios.</span><span class="sxs-lookup"><span data-stu-id="ed433-104">As a result, non-ASCII characters (characters whose ASCII codes are greater than 0x7F) are represented by two random characters.</span></span><p/><span data-ttu-id="ed433-105">Para aplicativos direcionados ao .NET Framework 4.5 ou posteriores e executados no .NET Framework 4.5.2, o `DataObject.GetData` recupera dados formatados em HTML como UTF-8, que representam caracteres maiores que 0x7F corretamente.</span><span class="sxs-lookup"><span data-stu-id="ed433-105">For apps that target the .NET Framework 4.5 or later and run on the .NET Framework 4.5.2, `DataObject.GetData` retrieves HTML-formatted data as UTF-8, which represents characters greater than 0x7F correctly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ed433-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="ed433-106">Suggestion</span></span>

<span data-ttu-id="ed433-107">Se você implementou uma solução alternativa para o problema de codificação com cadeias de caracteres formatadas em HTML (por exemplo, codificando explicitamente a cadeia de caracteres HTML recuperada da área de transferência enviando-a para <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>) e estiver redirecionando seu aplicativo da versão 4 para a versão 4.5, essa solução deverá ser removida. Se o comportamento antigo for necessário por algum motivo, o aplicativo poderá ser destinado ao .NET Framework 4.0 para obtê-lo.</span><span class="sxs-lookup"><span data-stu-id="ed433-107">If you implemented a workaround for the encoding problem with HTML-formatted strings (for example, by explicitly encoding the HTML string retrieved from the Clipboard by passing it to <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>) and you're retargeting your app from version 4 to 4.5, that workaround should be removed.If the old behavior is needed for some reason, the app can target the .NET Framework 4.0 to get that behavior.</span></span>

| <span data-ttu-id="ed433-108">Name</span><span class="sxs-lookup"><span data-stu-id="ed433-108">Name</span></span>    | <span data-ttu-id="ed433-109">Valor</span><span class="sxs-lookup"><span data-stu-id="ed433-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ed433-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="ed433-110">Scope</span></span>   | <span data-ttu-id="ed433-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="ed433-111">Edge</span></span>        |
| <span data-ttu-id="ed433-112">Versão</span><span class="sxs-lookup"><span data-stu-id="ed433-112">Version</span></span> | <span data-ttu-id="ed433-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="ed433-113">4.5.2</span></span>       |
| <span data-ttu-id="ed433-114">Type</span><span class="sxs-lookup"><span data-stu-id="ed433-114">Type</span></span>    | <span data-ttu-id="ed433-115">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="ed433-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ed433-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ed433-116">Affected APIs</span></span>

- <xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType>
- <xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType>
- <xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType>
