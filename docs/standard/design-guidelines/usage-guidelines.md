---
title: Diretrizes de uso
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04e44a6b58fd334b6a23e113922b980f69de627b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869860"
---
# <a name="usage-guidelines"></a><span data-ttu-id="ce86f-102">Diretrizes de uso</span><span class="sxs-lookup"><span data-stu-id="ce86f-102">Usage guidelines</span></span>

<span data-ttu-id="ce86f-103">Esta seção contém diretrizes para usar tipos comuns em APIs publicamente acessíveis.</span><span class="sxs-lookup"><span data-stu-id="ce86f-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="ce86f-104">Ele lida com o uso direto de tipos de estrutura (por exemplo, atributos de serialização) internas e operadores comuns de sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="ce86f-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="ce86f-105">O <xref:System.IDisposable?displayProperty=nameWithType> interface não é abordada nesta seção, mas é discutida a [padrão de descarte](../../../docs/standard/design-guidelines/dispose-pattern.md) seção.</span><span class="sxs-lookup"><span data-stu-id="ce86f-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="ce86f-106">Para obter diretrizes e informações adicionais sobre o sobre outro comum, tipos internos do .NET Framework, consulte os tópicos de referência para o seguinte: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ce86f-106">For guidelines and additional information about about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ce86f-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ce86f-107">In this section</span></span>

[<span data-ttu-id="ce86f-108">Matrizes</span><span class="sxs-lookup"><span data-stu-id="ce86f-108">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="ce86f-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="ce86f-109">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="ce86f-110">Coleções</span><span class="sxs-lookup"><span data-stu-id="ce86f-110">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="ce86f-111">Serialização</span><span class="sxs-lookup"><span data-stu-id="ce86f-111">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="ce86f-112">Uso de System.XML</span><span class="sxs-lookup"><span data-stu-id="ce86f-112">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="ce86f-113">Operadores de igualdade</span><span class="sxs-lookup"><span data-stu-id="ce86f-113">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="ce86f-114">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="ce86f-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="ce86f-115">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="ce86f-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ce86f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce86f-116">See also</span></span>

- [<span data-ttu-id="ce86f-117">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="ce86f-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
