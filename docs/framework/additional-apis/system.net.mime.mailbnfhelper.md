---
title: Classe MailBnfHelper (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mime.MailBnfHelper
- System.Net.Mime.MailBnfHelper.Ascii7bitMaxValue
- System.Net.Mime.MailBnfHelper.Atext
- System.Net.Mime.MailBnfHelper.CR
- System.Net.Mime.MailBnfHelper.Ctext
- System.Net.Mime.MailBnfHelper.Dot
- System.Net.Mime.MailBnfHelper.EndComment
- System.Net.Mime.MailBnfHelper.LF
- System.Net.Mime.MailBnfHelper.Space
- System.Net.Mime.MailBnfHelper.StartComment
- System.Net.Mime.MailBnfHelper.Tab
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 86c98726a7886285917b6be8c7631ca1e9e425e6
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990296"
---
# <a name="mailbnfhelper-class"></a><span data-ttu-id="a9641-102">Classe MailBnfHelper</span><span class="sxs-lookup"><span data-stu-id="a9641-102">MailBnfHelper class</span></span>

<span data-ttu-id="a9641-103">Contém métodos de utilitário para análise de cadeias de caracteres formatadas por mensagem da Internet.</span><span class="sxs-lookup"><span data-stu-id="a9641-103">Contains utility methods for parsing internet message-formatted strings.</span></span> <span data-ttu-id="a9641-104">Esta classe não pode ser herdada.</span><span class="sxs-lookup"><span data-stu-id="a9641-104">This class cannot be inherited.</span></span>

```csharp
internal static class MailBnfHelper
```

> [!WARNING]
> <span data-ttu-id="a9641-105">Essa classe é interna e não deve ser usada diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="a9641-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a9641-106">A Microsoft não oferece suporte ao uso dessa classe em um aplicativo de produção em nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="a9641-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="ascii7bitmaxvalue-field"></a><span data-ttu-id="a9641-107">Campo Ascii7bitMaxValue</span><span class="sxs-lookup"><span data-stu-id="a9641-107">Ascii7bitMaxValue field</span></span>

<span data-ttu-id="a9641-108">Representa o valor ASCII máximo de 7 bits.</span><span class="sxs-lookup"><span data-stu-id="a9641-108">Represents the maximum 7-bit Ascii value.</span></span>

```csharp
internal static readonly int Ascii7bitMaxValue
```

## <a name="atext-field"></a><span data-ttu-id="a9641-109">Campo Atext</span><span class="sxs-lookup"><span data-stu-id="a9641-109">Atext field</span></span>

<span data-ttu-id="a9641-110">Representa os caracteres permitidos em Atoms.</span><span class="sxs-lookup"><span data-stu-id="a9641-110">Represents the characters allowed in atoms.</span></span>

```csharp
internal static bool[] Atext
```

## <a name="cr-field"></a><span data-ttu-id="a9641-111">Campo CR</span><span class="sxs-lookup"><span data-stu-id="a9641-111">CR field</span></span>

<span data-ttu-id="a9641-112">Representa o caractere de retorno de carro.</span><span class="sxs-lookup"><span data-stu-id="a9641-112">Represents the carriage-return character.</span></span>

```csharp
internal static readonly char CR
```

## <a name="ctext-field"></a><span data-ttu-id="a9641-113">Campo CTEXT</span><span class="sxs-lookup"><span data-stu-id="a9641-113">Ctext field</span></span>

<span data-ttu-id="a9641-114">Representa os caracteres permitidos dentro de comentários.</span><span class="sxs-lookup"><span data-stu-id="a9641-114">Represents the characters allowed inside of comments.</span></span>

```csharp
internal static bool[] Ctext
```

## <a name="dot-field"></a><span data-ttu-id="a9641-115">Campo de ponto</span><span class="sxs-lookup"><span data-stu-id="a9641-115">Dot field</span></span>

<span data-ttu-id="a9641-116">Representa o caractere de parada completa ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="a9641-116">Represents the full-stop character (`.`).</span></span>

```csharp
internal static readonly char Dot
```

## <a name="endcomment-field"></a><span data-ttu-id="a9641-117">Campo endcomment</span><span class="sxs-lookup"><span data-stu-id="a9641-117">EndComment field</span></span>

<span data-ttu-id="a9641-118">Representa o caractere que especifica o final de um comentário.</span><span class="sxs-lookup"><span data-stu-id="a9641-118">Represents the character that specifies the end of a comment.</span></span>

```csharp
internal static readonly char EndComment
```

## <a name="lf-field"></a><span data-ttu-id="a9641-119">Campo LF</span><span class="sxs-lookup"><span data-stu-id="a9641-119">LF field</span></span>

<span data-ttu-id="a9641-120">Representa o caractere de alimentação de linha.</span><span class="sxs-lookup"><span data-stu-id="a9641-120">Represents the line-feed character.</span></span>

```csharp
internal static readonly char LF
```

## <a name="space-field"></a><span data-ttu-id="a9641-121">Campo de espaço</span><span class="sxs-lookup"><span data-stu-id="a9641-121">Space field</span></span>

<span data-ttu-id="a9641-122">Representa o caractere de espaço.</span><span class="sxs-lookup"><span data-stu-id="a9641-122">Represents the space character.</span></span>

```csharp
internal static readonly char Space
```

## <a name="startcomment-field"></a><span data-ttu-id="a9641-123">Campo StartComment</span><span class="sxs-lookup"><span data-stu-id="a9641-123">StartComment field</span></span>

<span data-ttu-id="a9641-124">Representa o caractere que especifica o início de um comentário.</span><span class="sxs-lookup"><span data-stu-id="a9641-124">Represents the character that specifies the start of a comment.</span></span>

```csharp
internal static readonly char StartComment
```

## <a name="tab-field"></a><span data-ttu-id="a9641-125">Campo de guia</span><span class="sxs-lookup"><span data-stu-id="a9641-125">Tab field</span></span>

<span data-ttu-id="a9641-126">Representa o caractere de tabulação.</span><span class="sxs-lookup"><span data-stu-id="a9641-126">Represents the tab character.</span></span>

```csharp
internal static readonly char Tab
```

## <a name="requirements"></a><span data-ttu-id="a9641-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a9641-127">Requirements</span></span>

<span data-ttu-id="a9641-128">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="a9641-128">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="a9641-129">**Assembly:** Sistema (em System.dll)</span><span class="sxs-lookup"><span data-stu-id="a9641-129">**Assembly:** System (in System.dll)</span></span>
