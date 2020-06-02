---
title: Design de classe estática
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: c906502ed071e8515f101996ec42a04772f72b12
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291923"
---
# <a name="static-class-design"></a><span data-ttu-id="ea8aa-102">Design de classe estática</span><span class="sxs-lookup"><span data-stu-id="ea8aa-102">Static Class Design</span></span>
<span data-ttu-id="ea8aa-103">Uma classe estática é definida como uma classe que contém somente membros estáticos (é claro além dos membros da instância herdados de <xref:System.Object?displayProperty=nameWithType> e possivelmente um Construtor privado).</span><span class="sxs-lookup"><span data-stu-id="ea8aa-103">A static class is defined as a class that contains only static members (of course besides the instance members inherited from <xref:System.Object?displayProperty=nameWithType> and possibly a private constructor).</span></span> <span data-ttu-id="ea8aa-104">Algumas linguagens fornecem suporte interno para classes estáticas.</span><span class="sxs-lookup"><span data-stu-id="ea8aa-104">Some languages provide built-in support for static classes.</span></span> <span data-ttu-id="ea8aa-105">No C# 2,0 e posterior, quando uma classe é declarada como estática, ela é sealed, abstract e nenhum membro de instância pode ser substituído ou declarado.</span><span class="sxs-lookup"><span data-stu-id="ea8aa-105">In C# 2.0 and later, when a class is declared to be static, it is sealed, abstract, and no instance members can be overridden or declared.</span></span>

 <span data-ttu-id="ea8aa-106">As classes estáticas são um compromisso entre o design puro orientado a objeto e a simplicidade.</span><span class="sxs-lookup"><span data-stu-id="ea8aa-106">Static classes are a compromise between pure object-oriented design and simplicity.</span></span> <span data-ttu-id="ea8aa-107">Normalmente, eles são usados para fornecer atalhos para outras operações (como <xref:System.IO.File?displayProperty=nameWithType> ), os proprietários de métodos de extensão ou a funcionalidade para a qual um wrapper completo orientado a objeto não é garantido (como <xref:System.Environment?displayProperty=nameWithType> ).</span><span class="sxs-lookup"><span data-stu-id="ea8aa-107">They are commonly used to provide shortcuts to other operations (such as <xref:System.IO.File?displayProperty=nameWithType>), holders of extension methods, or functionality for which a full object-oriented wrapper is unwarranted (such as <xref:System.Environment?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="ea8aa-108">✔️ usar classes estáticas com moderação.</span><span class="sxs-lookup"><span data-stu-id="ea8aa-108">✔️ DO use static classes sparingly.</span></span>

 <span data-ttu-id="ea8aa-109">Classes estáticas devem ser usadas somente como classes de suporte para o núcleo orientado a objeto da estrutura.</span><span class="sxs-lookup"><span data-stu-id="ea8aa-109">Static classes should be used only as supporting classes for the object-oriented core of the framework.</span></span>

 <span data-ttu-id="ea8aa-110">❌Não trate classes estáticas como um Bucket variado.</span><span class="sxs-lookup"><span data-stu-id="ea8aa-110">❌ DO NOT treat static classes as a miscellaneous bucket.</span></span>

 <span data-ttu-id="ea8aa-111">❌Não declare nem substitua membros de instância em classes estáticas.</span><span class="sxs-lookup"><span data-stu-id="ea8aa-111">❌ DO NOT declare or override instance members in static classes.</span></span>

 <span data-ttu-id="ea8aa-112">✔️ declare classes estáticas como lacradas, abstratas e adicione um construtor de instância privada se a linguagem de programação não tiver suporte interno para classes estáticas.</span><span class="sxs-lookup"><span data-stu-id="ea8aa-112">✔️ DO declare static classes as sealed, abstract, and add a private instance constructor if your programming language does not have built-in support for static classes.</span></span>

 <span data-ttu-id="ea8aa-113">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="ea8aa-113">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ea8aa-114">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="ea8aa-114">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ea8aa-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="ea8aa-115">See also</span></span>

- [<span data-ttu-id="ea8aa-116">Diretrizes de design de tipo</span><span class="sxs-lookup"><span data-stu-id="ea8aa-116">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="ea8aa-117">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="ea8aa-117">Framework Design Guidelines</span></span>](index.md)
