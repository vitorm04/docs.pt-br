---
title: Aviso de SYSLIB0001
description: Saiba mais sobre o obsoletions que gera SYSLIB0001 de aviso de tempo de compilação.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: d38d915e902d3c37cc461452f805e8349f11deeb
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439983"
---
# <a name="syslib0001-the-utf-7-encoding-is-insecure"></a><span data-ttu-id="4fa4c-103">SYSLIB0001: a codificação UTF-7 é insegura</span><span class="sxs-lookup"><span data-stu-id="4fa4c-103">SYSLIB0001: The UTF-7 encoding is insecure</span></span>

<span data-ttu-id="4fa4c-104">A codificação UTF-7 não está mais em uso amplo entre aplicativos, e muitas especificações agora [proíbem seu uso](https://security.stackexchange.com/a/68609/3573) no intercâmbio.</span><span class="sxs-lookup"><span data-stu-id="4fa4c-104">The UTF-7 encoding is no longer in wide use among applications, and many specs now [forbid its use](https://security.stackexchange.com/a/68609/3573) in interchange.</span></span> <span data-ttu-id="4fa4c-105">Ele também é [usado ocasionalmente como um vetor de ataque](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) em aplicativos que não antecipam a ocorrência de dados codificados em UTF-7.</span><span class="sxs-lookup"><span data-stu-id="4fa4c-105">It's also occasionally [used as an attack vector](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) in applications that don't anticipate encountering UTF-7-encoded data.</span></span> <span data-ttu-id="4fa4c-106">A Microsoft avisa sobre o uso do <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> porque não fornece detecção de erros.</span><span class="sxs-lookup"><span data-stu-id="4fa4c-106">Microsoft warns against use of <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> because it doesn't provide error detection.</span></span>

<span data-ttu-id="4fa4c-107">Consequentemente, as seguintes APIs são marcadas como obsoletas, a partir do .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="4fa4c-107">Consequently, the following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="4fa4c-108">O uso dessas APIs gera aviso `SYSLIB0001` no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="4fa4c-108">Use of these APIs generates warning `SYSLIB0001` at compile time.</span></span>

- <span data-ttu-id="4fa4c-109">Propriedade <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4fa4c-109"><xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property</span></span>
- <span data-ttu-id="4fa4c-110"><xref:System.Text.UTF7Encoding.%23ctor%2A> construtores</span><span class="sxs-lookup"><span data-stu-id="4fa4c-110"><xref:System.Text.UTF7Encoding.%23ctor%2A> constructors</span></span>

## <a name="workarounds"></a><span data-ttu-id="4fa4c-111">Soluções Alternativas</span><span class="sxs-lookup"><span data-stu-id="4fa4c-111">Workarounds</span></span>

- <span data-ttu-id="4fa4c-112">Se você estiver usando <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> ou <xref:System.Text.UTF7Encoding> dentro de seu próprio protocolo ou formato de arquivo:</span><span class="sxs-lookup"><span data-stu-id="4fa4c-112">If you're using <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding> within your own protocol or file format:</span></span>

  <span data-ttu-id="4fa4c-113">Alterne para o usando o <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> ou o <xref:System.Text.UTF8Encoding> .</span><span class="sxs-lookup"><span data-stu-id="4fa4c-113">Switch to using <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> or <xref:System.Text.UTF8Encoding>.</span></span> <span data-ttu-id="4fa4c-114">O UTF-8 é um padrão da indústria e tem amplo suporte em linguagens, sistemas operacionais e tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="4fa4c-114">UTF-8 is an industry standard and is widely supported across languages, operating systems, and runtimes.</span></span> <span data-ttu-id="4fa4c-115">O uso de UTF-8 facilita a manutenção futura de seu código e o torna mais interoperável com o restante do ecossistema.</span><span class="sxs-lookup"><span data-stu-id="4fa4c-115">Using UTF-8 eases future maintenance of your code and makes it more interoperable with the rest of the ecosystem.</span></span>

- <span data-ttu-id="4fa4c-116">Se você estiver comparando uma <xref:System.Text.Encoding> instância do <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="4fa4c-116">If you're comparing an <xref:System.Text.Encoding> instance against <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>:</span></span>

  <span data-ttu-id="4fa4c-117">Em vez disso, considere executar uma verificação na página de código UTF-7 conhecida, que é `65000` .</span><span class="sxs-lookup"><span data-stu-id="4fa4c-117">Instead, consider performing a check against the well-known UTF-7 code page, which is `65000`.</span></span> <span data-ttu-id="4fa4c-118">Ao comparar com a página de código, você evita o aviso e também lida com alguns casos de borda, como se alguém chamou `new UTF7Encoding()` ou subclasse o tipo.</span><span class="sxs-lookup"><span data-stu-id="4fa4c-118">By comparing against the code page, you avoid the warning and also handle some edge cases, such as if somebody called `new UTF7Encoding()` or subclassed the type.</span></span>

  ```csharp
  void DoSomething(Encoding enc)
  {
      // Don't perform the check this way.
      // It produces a warning and misses some edge cases.
      if (enc == Encoding.UTF7)
      {
          // Encoding is UTF-7.
      }

      // Instead, perform the check this way.
      if (enc != null && enc.CodePage == 65000)
      {
          // Encoding is UTF-7.
      }
  }
  ```

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="4fa4c-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="4fa4c-119">See also</span></span>

- [<span data-ttu-id="4fa4c-120">Os caminhos de código UTF-7 estão obsoletos</span><span class="sxs-lookup"><span data-stu-id="4fa4c-120">UTF-7 code paths are obsolete</span></span>](3.1-5.0.md#utf-7-code-paths-are-obsolete)
