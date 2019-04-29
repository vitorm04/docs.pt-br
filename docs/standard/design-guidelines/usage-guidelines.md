---
title: Diretrizes de uso
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
author: KrzysztofCwalina
ms.openlocfilehash: 761570b899a2a36391eb81dc7f42e13fff1f14ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778800"
---
# <a name="usage-guidelines"></a><span data-ttu-id="522d6-102">Diretrizes de uso</span><span class="sxs-lookup"><span data-stu-id="522d6-102">Usage guidelines</span></span>

<span data-ttu-id="522d6-103">Esta seção contém diretrizes para usar tipos comuns em APIs publicamente acessíveis.</span><span class="sxs-lookup"><span data-stu-id="522d6-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="522d6-104">Ele lida com o uso direto de tipos de estrutura (por exemplo, atributos de serialização) internas e operadores comuns de sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="522d6-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="522d6-105">O <xref:System.IDisposable?displayProperty=nameWithType> interface não é abordada nesta seção, mas é discutida a [padrão de descarte](../../../docs/standard/design-guidelines/dispose-pattern.md) seção.</span><span class="sxs-lookup"><span data-stu-id="522d6-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="522d6-106">Para obter diretrizes e informações adicionais sobre outro comum, tipos internos do .NET Framework, consulte os tópicos de referência para o seguinte: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="522d6-106">For guidelines and additional information about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="522d6-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="522d6-107">In this section</span></span>

[<span data-ttu-id="522d6-108">Matrizes</span><span class="sxs-lookup"><span data-stu-id="522d6-108">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="522d6-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="522d6-109">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="522d6-110">Coleções</span><span class="sxs-lookup"><span data-stu-id="522d6-110">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="522d6-111">Serialização</span><span class="sxs-lookup"><span data-stu-id="522d6-111">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="522d6-112">Uso de System.XML</span><span class="sxs-lookup"><span data-stu-id="522d6-112">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="522d6-113">Operadores de igualdade</span><span class="sxs-lookup"><span data-stu-id="522d6-113">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="522d6-114">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="522d6-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="522d6-115">*Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="522d6-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="522d6-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="522d6-116">See also</span></span>

- [<span data-ttu-id="522d6-117">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="522d6-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
