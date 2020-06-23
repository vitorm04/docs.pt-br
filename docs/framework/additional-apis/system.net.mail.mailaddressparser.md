---
title: Classe MailAddressParser (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.MailAddressParser
- System.Net.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 2c17970614ff9b6f1e6793a064a956da7248d693
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990301"
---
# <a name="mailaddressparser-class"></a><span data-ttu-id="b39d7-102">Classe MailAddressParser</span><span class="sxs-lookup"><span data-stu-id="b39d7-102">MailAddressParser class</span></span>

<span data-ttu-id="b39d7-103">Analisa endereços de email conforme descrito em RFC 2822.</span><span class="sxs-lookup"><span data-stu-id="b39d7-103">Parses email addresses as described in RFC 2822.</span></span> <span data-ttu-id="b39d7-104">Esta classe não pode ser herdada.</span><span class="sxs-lookup"><span data-stu-id="b39d7-104">This class cannot be inherited.</span></span>

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> <span data-ttu-id="b39d7-105">Essa classe é interna e não deve ser usada diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="b39d7-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="b39d7-106">A Microsoft não oferece suporte ao uso dessa classe em um aplicativo de produção em nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="b39d7-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="parseaddress-method"></a><span data-ttu-id="b39d7-107">Método ParseAddress</span><span class="sxs-lookup"><span data-stu-id="b39d7-107">ParseAddress method</span></span>

<span data-ttu-id="b39d7-108">Analisa um único endereço de email da cadeia de caracteres especificada.</span><span class="sxs-lookup"><span data-stu-id="b39d7-108">Parses a single email address from the specified string.</span></span>

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a><span data-ttu-id="b39d7-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b39d7-109">Parameters</span></span>

<span data-ttu-id="b39d7-110">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b39d7-110">`data` <xref:System.String></span></span>

<span data-ttu-id="b39d7-111">A cadeia de caracteres que contém um endereço de email a ser analisado.</span><span class="sxs-lookup"><span data-stu-id="b39d7-111">The string that contains an email address to be parsed.</span></span>

### <a name="return-value"></a><span data-ttu-id="b39d7-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b39d7-112">Return value</span></span>

<xref:System.Net.Mail.MailAddress>

<span data-ttu-id="b39d7-113">Um endereço de email válido.</span><span class="sxs-lookup"><span data-stu-id="b39d7-113">A valid email address.</span></span>

### <a name="exceptions"></a><span data-ttu-id="b39d7-114">Exceções</span><span class="sxs-lookup"><span data-stu-id="b39d7-114">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="b39d7-115">O endereço de email é inválido.</span><span class="sxs-lookup"><span data-stu-id="b39d7-115">The email address is invalid.</span></span>

## <a name="requirements"></a><span data-ttu-id="b39d7-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b39d7-116">Requirements</span></span>

<span data-ttu-id="b39d7-117">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="b39d7-117">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="b39d7-118">**Assembly:** Sistema (em System.dll)</span><span class="sxs-lookup"><span data-stu-id="b39d7-118">**Assembly:** System (in System.dll)</span></span>
