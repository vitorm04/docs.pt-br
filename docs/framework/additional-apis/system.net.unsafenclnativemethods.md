---
title: Classe UnsafeNclNativeMethods (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.UnsafeNclNativeMethods
- System.Net.UnsafeNclNativeMethods.NativePKI
- System.Net.UnsafeNclNativeMethods.NativePKI.FindClientCertificates
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 46756a0d1d69b4768dbb8dcdd7ab098d3f1849bf
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990293"
---
# <a name="unsafenclnativemethods-class"></a><span data-ttu-id="5fd66-102">Classe UnsafeNclNativeMethods</span><span class="sxs-lookup"><span data-stu-id="5fd66-102">UnsafeNclNativeMethods class</span></span>

<span data-ttu-id="5fd66-103">Contém classes que importam métodos de rede nativas não seguros.</span><span class="sxs-lookup"><span data-stu-id="5fd66-103">Contains classes that import unsafe native networking methods.</span></span> <span data-ttu-id="5fd66-104">Esta classe não pode ser herdada.</span><span class="sxs-lookup"><span data-stu-id="5fd66-104">This class cannot be inherited.</span></span>

```csharp
internal static class UnsafeNclNativeMethods
```

> [!WARNING]
> <span data-ttu-id="5fd66-105">Essa classe é interna e não deve ser usada diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="5fd66-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="5fd66-106">A Microsoft não oferece suporte ao uso dessa classe em um aplicativo de produção em nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="5fd66-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="nativepki-class"></a><span data-ttu-id="5fd66-107">Classe NativePKI</span><span class="sxs-lookup"><span data-stu-id="5fd66-107">NativePKI class</span></span>

<span data-ttu-id="5fd66-108">Contém métodos importados do crypt32.dll.</span><span class="sxs-lookup"><span data-stu-id="5fd66-108">Contains methods imported from crypt32.dll.</span></span> <span data-ttu-id="5fd66-109">Esses métodos manipulam certificados ao usar o protocolo HTTPS (Hypertext Transfer Protocol Secure).</span><span class="sxs-lookup"><span data-stu-id="5fd66-109">These methods handle certificates when using Hypertext Transfer Protocol Secure (HTTPS).</span></span> <span data-ttu-id="5fd66-110">Esta classe não pode ser herdada.</span><span class="sxs-lookup"><span data-stu-id="5fd66-110">This class cannot be inherited.</span></span>

```csharp
internal static class NativePKI
```

## <a name="nativepkifindclientcertificates-method"></a><span data-ttu-id="5fd66-111">Método NativePKI. FindClientCertificates</span><span class="sxs-lookup"><span data-stu-id="5fd66-111">NativePKI.FindClientCertificates method</span></span>

<span data-ttu-id="5fd66-112">Descobre os certificados de cliente disponíveis para enviar ao servidor.</span><span class="sxs-lookup"><span data-stu-id="5fd66-112">Discovers available client certificates to send to the server.</span></span>

```csharp
internal static X509CertificateCollection FindClientCertificates
```

### <a name="return-value"></a><span data-ttu-id="5fd66-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="5fd66-113">Return value</span></span>

<xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection?displayProperty=nameWithType>

<span data-ttu-id="5fd66-114">Uma coleção de certificados de cliente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="5fd66-114">A collection of available client certificates.</span></span>

## <a name="requirements"></a><span data-ttu-id="5fd66-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5fd66-115">Requirements</span></span>

<span data-ttu-id="5fd66-116">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="5fd66-116">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="5fd66-117">**Assembly:** Sistema (em System.dll)</span><span class="sxs-lookup"><span data-stu-id="5fd66-117">**Assembly:** System (in System.dll)</span></span>
