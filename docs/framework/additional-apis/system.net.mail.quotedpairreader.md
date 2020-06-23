---
title: Classe QuotedPairReader (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.QuotedPairReader
- System.Net.QuotedPairReader.CountQuotedChars
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 9b0bf835a34eecc651894f4336648b73a81b665c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990297"
---
# <a name="quotedpairreader-class"></a><span data-ttu-id="a2821-102">Classe QuotedPairReader</span><span class="sxs-lookup"><span data-stu-id="a2821-102">QuotedPairReader class</span></span>

<span data-ttu-id="a2821-103">Determina quais caracteres são colocados entre aspas (escape) em uma cadeia de caracteres entre aspas.</span><span class="sxs-lookup"><span data-stu-id="a2821-103">Determines which characters are quoted (escaped) in a quoted string.</span></span> <span data-ttu-id="a2821-104">Esta classe não pode ser herdada.</span><span class="sxs-lookup"><span data-stu-id="a2821-104">This class cannot be inherited.</span></span>

```csharp
internal static class QuotedPairReader
```

> [!WARNING]
> <span data-ttu-id="a2821-105">Essa classe é interna e não deve ser usada diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="a2821-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a2821-106">A Microsoft não oferece suporte ao uso dessa classe em um aplicativo de produção em nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="a2821-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="countquotedchars-method"></a><span data-ttu-id="a2821-107">Método CountQuotedChars</span><span class="sxs-lookup"><span data-stu-id="a2821-107">CountQuotedChars method</span></span>

<span data-ttu-id="a2821-108">Conta o número de caracteres entre aspas consecutivas, incluindo várias barras invertidas precedentes, na cadeia de caracteres especificada.</span><span class="sxs-lookup"><span data-stu-id="a2821-108">Counts the number of consecutive quoted characters, including multiple preceding quoted backslashes, in the specified string.</span></span> <span data-ttu-id="a2821-109">Por exemplo, considerando a cadeia `a\\\b` de caracteres e um índice de `4` , o método retorna `4` , porque `b` está entre aspas e, portanto, as três barras invertidas precedentes.</span><span class="sxs-lookup"><span data-stu-id="a2821-109">For example, given the string `a\\\b` and an index of `4`, the method returns `4`, because `b` is quoted and so are the three preceding backslashes.</span></span>

```csharp
internal static int CountQuotedChars(string data, int index, bool permitUnicodeEscaping)
```

### <a name="parameters"></a><span data-ttu-id="a2821-110">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a2821-110">Parameters</span></span>

- <span data-ttu-id="a2821-111">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a2821-111">`data` <xref:System.String></span></span>

  <span data-ttu-id="a2821-112">A cadeia de dados na qual contar caracteres entre aspas consecutivas.</span><span class="sxs-lookup"><span data-stu-id="a2821-112">The data string in which to count consecutive quoted characters.</span></span>

- <span data-ttu-id="a2821-113">`index` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="a2821-113">`index` <xref:System.Int32></span></span>

  <span data-ttu-id="a2821-114">A posição na cadeia de caracteres especificada até e incluindo quais caracteres entre aspas consecutivas devem ser contados.</span><span class="sxs-lookup"><span data-stu-id="a2821-114">The position in the specified string up to and including which consecutive quoted characters should be counted.</span></span>

- <span data-ttu-id="a2821-115">`permitUnicodeEscaping` <xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="a2821-115">`permitUnicodeEscaping` <xref:System.Boolean></span></span>

  <span data-ttu-id="a2821-116">`true`para permitir que os caracteres Unicode sejam ignorados; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="a2821-116">`true` to permit Unicode characters to be escaped; otherwise, `false`.</span></span>

### <a name="return-value"></a><span data-ttu-id="a2821-117">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a2821-117">Return value</span></span>

<xref:System.Int32?displayProperty=nameWithType>

<span data-ttu-id="a2821-118">`0`Se o caractere no índice especificado não for de escape; caso contrário, o número de caracteres entre aspas consecutivas até e incluindo o caractere em `index` .</span><span class="sxs-lookup"><span data-stu-id="a2821-118">`0` if the character at the specified index is not escaped; otherwise, the number of consecutive quoted characters up to and including the character at `index`.</span></span>

### <a name="exceptions"></a><span data-ttu-id="a2821-119">Exceções</span><span class="sxs-lookup"><span data-stu-id="a2821-119">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="a2821-120">Um caractere Unicode de escape foi encontrado, mas não é permitido.</span><span class="sxs-lookup"><span data-stu-id="a2821-120">An escaped Unicode character was found but is not permitted.</span></span>

## <a name="requirements"></a><span data-ttu-id="a2821-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a2821-121">Requirements</span></span>

<span data-ttu-id="a2821-122">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="a2821-122">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="a2821-123">**Assembly:** Sistema (em System.dll)</span><span class="sxs-lookup"><span data-stu-id="a2821-123">**Assembly:** System (in System.dll)</span></span>
