---
title: Design de campo
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: c00929ca499e39bd4e24d482c9413beb9cccddc1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741602"
---
# <a name="field-design"></a><span data-ttu-id="9abc1-102">Design de campo</span><span class="sxs-lookup"><span data-stu-id="9abc1-102">Field Design</span></span>
<span data-ttu-id="9abc1-103">O princípio do encapsulamento é uma das noções mais importantes no design orientado a objeto.</span><span class="sxs-lookup"><span data-stu-id="9abc1-103">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="9abc1-104">Esse princípio determina que os dados armazenados dentro de um objeto devem ser acessíveis somente para esse objeto.</span><span class="sxs-lookup"><span data-stu-id="9abc1-104">This principle states that data stored inside an object should be accessible only to that object.</span></span>

 <span data-ttu-id="9abc1-105">Uma maneira útil de interpretar o princípio é dizer que um tipo deve ser projetado de forma que as alterações em campos desse tipo (nome ou alterações de tipo) possam ser feitas sem a quebra de código além dos membros do tipo.</span><span class="sxs-lookup"><span data-stu-id="9abc1-105">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="9abc1-106">Essa interpretação implica imediatamente que todos os campos devem ser privados.</span><span class="sxs-lookup"><span data-stu-id="9abc1-106">This interpretation immediately implies that all fields must be private.</span></span>

 <span data-ttu-id="9abc1-107">Nós excluímos campos somente leitura e constantes da constante, pois esses campos, quase por definição, nunca precisam ser alterados.</span><span class="sxs-lookup"><span data-stu-id="9abc1-107">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>

 <span data-ttu-id="9abc1-108">❌ não fornecem campos de instância públicos ou protegidos.</span><span class="sxs-lookup"><span data-stu-id="9abc1-108">❌ DO NOT provide instance fields that are public or protected.</span></span>

 <span data-ttu-id="9abc1-109">Você deve fornecer propriedades para acessar campos em vez de torná-las públicas ou protegidas.</span><span class="sxs-lookup"><span data-stu-id="9abc1-109">You should provide properties for accessing fields instead of making them public or protected.</span></span>

 <span data-ttu-id="9abc1-110">✔️ usar campos constantes para constantes que nunca serão alteradas.</span><span class="sxs-lookup"><span data-stu-id="9abc1-110">✔️ DO use constant fields for constants that will never change.</span></span>

 <span data-ttu-id="9abc1-111">O compilador grava os valores de campos const diretamente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="9abc1-111">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="9abc1-112">Portanto, os valores const nunca podem ser alterados sem o risco de perder a compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="9abc1-112">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>

 <span data-ttu-id="9abc1-113">✔️ Use campos públicos estáticos `readonly` para instâncias de objetos predefinidas.</span><span class="sxs-lookup"><span data-stu-id="9abc1-113">✔️ DO use public static `readonly` fields for predefined object instances.</span></span>

 <span data-ttu-id="9abc1-114">Se houver instâncias predefinidas do tipo, declare-as como campos estáticos somente leitura públicos do próprio tipo.</span><span class="sxs-lookup"><span data-stu-id="9abc1-114">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>

 <span data-ttu-id="9abc1-115">❌ não atribua instâncias de tipos mutáveis a campos `readonly`.</span><span class="sxs-lookup"><span data-stu-id="9abc1-115">❌ DO NOT assign instances of mutable types to `readonly` fields.</span></span>

 <span data-ttu-id="9abc1-116">Um tipo mutável é um tipo com instâncias que podem ser modificadas depois de terem sido instanciadas.</span><span class="sxs-lookup"><span data-stu-id="9abc1-116">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="9abc1-117">Por exemplo, matrizes, a maioria das coleções e fluxos são tipos mutáveis, mas <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>e <xref:System.String?displayProperty=nameWithType> são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="9abc1-117">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="9abc1-118">O modificador somente leitura em um campo de tipo de referência impede que a instância armazenada no campo seja substituída, mas não impede que os dados de instância do campo sejam modificados chamando Membros que alteram a instância.</span><span class="sxs-lookup"><span data-stu-id="9abc1-118">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>

 <span data-ttu-id="9abc1-119">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="9abc1-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="9abc1-120">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="9abc1-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="9abc1-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="9abc1-121">See also</span></span>

- [<span data-ttu-id="9abc1-122">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="9abc1-122">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="9abc1-123">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="9abc1-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
