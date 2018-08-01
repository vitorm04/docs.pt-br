---
title: Design de campo
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d47934c3fed17f75a97ef5da0397c6ceba53d68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571105"
---
# <a name="field-design"></a><span data-ttu-id="d7f68-102">Design de campo</span><span class="sxs-lookup"><span data-stu-id="d7f68-102">Field Design</span></span>
<span data-ttu-id="d7f68-103">O princípio de encapsulamento é um dos conceitos mais importantes no design orientado a objeto.</span><span class="sxs-lookup"><span data-stu-id="d7f68-103">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="d7f68-104">Esse princípio afirma que os dados armazenados dentro de um objeto devem ser acessíveis somente para esse objeto.</span><span class="sxs-lookup"><span data-stu-id="d7f68-104">This principle states that data stored inside an object should be accessible only to that object.</span></span>  
  
 <span data-ttu-id="d7f68-105">Uma maneira útil de interpretar o princípio é dizer que um tipo deve ser projetado para que as alterações aos campos do tipo (alterações de nome ou tipo) podem ser feitas sem quebra de código diferente para os membros do tipo.</span><span class="sxs-lookup"><span data-stu-id="d7f68-105">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="d7f68-106">Essa interpretação imediatamente implica que todos os campos devem ser privados.</span><span class="sxs-lookup"><span data-stu-id="d7f68-106">This interpretation immediately implies that all fields must be private.</span></span>  
  
 <span data-ttu-id="d7f68-107">Excluímos constantes e estáticos campos somente leitura dessa restrição estrito, porque esses campos, quase por definição, nunca devem alterar.</span><span class="sxs-lookup"><span data-stu-id="d7f68-107">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>  
  
 <span data-ttu-id="d7f68-108">**X DO NOT** fornecem campos de instância público ou protegido.</span><span class="sxs-lookup"><span data-stu-id="d7f68-108">**X DO NOT** provide instance fields that are public or protected.</span></span>  
  
 <span data-ttu-id="d7f68-109">Você deve fornecer as propriedades para acessar os campos em vez de torná-los público ou protegido.</span><span class="sxs-lookup"><span data-stu-id="d7f68-109">You should provide properties for accessing fields instead of making them public or protected.</span></span>  
  
 <span data-ttu-id="d7f68-110">**✓ DO** usar campos de constantes para constantes que nunca serão alterado.</span><span class="sxs-lookup"><span data-stu-id="d7f68-110">**✓ DO** use constant fields for constants that will never change.</span></span>  
  
 <span data-ttu-id="d7f68-111">O compilador Superexpõe os valores dos campos constantes diretamente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="d7f68-111">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="d7f68-112">Portanto, os valores constantes nunca podem ser alterados sem o risco de perder a compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="d7f68-112">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>  
  
 <span data-ttu-id="d7f68-113">**✓ DO** usar estático público `readonly` campos para instâncias de objeto predefinido.</span><span class="sxs-lookup"><span data-stu-id="d7f68-113">**✓ DO** use public static `readonly` fields for predefined object instances.</span></span>  
  
 <span data-ttu-id="d7f68-114">Se houver instâncias predefinidas do tipo, declará-los como somente leitura estáticos campos públicos do próprio tipo.</span><span class="sxs-lookup"><span data-stu-id="d7f68-114">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>  
  
 <span data-ttu-id="d7f68-115">**X DO NOT** atribuir instâncias dos tipos mutáveis para `readonly` campos.</span><span class="sxs-lookup"><span data-stu-id="d7f68-115">**X DO NOT** assign instances of mutable types to `readonly` fields.</span></span>  
  
 <span data-ttu-id="d7f68-116">Um tipo mutável é um tipo com instâncias que podem ser modificados depois que eles são instanciados.</span><span class="sxs-lookup"><span data-stu-id="d7f68-116">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="d7f68-117">Por exemplo, os fluxos, a maioria das coleções e matrizes são tipos mutáveis, mas <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, e <xref:System.String?displayProperty=nameWithType> são todos imutável.</span><span class="sxs-lookup"><span data-stu-id="d7f68-117">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="d7f68-118">O modificador de somente leitura em um campo de tipo de referência impede que a instância armazenada no campo seja substituído, mas não impede que dados da instância do campo que está sendo modificado chamando membros alterando a instância.</span><span class="sxs-lookup"><span data-stu-id="d7f68-118">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>  
  
 <span data-ttu-id="d7f68-119">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="d7f68-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d7f68-120">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="d7f68-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7f68-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7f68-121">See Also</span></span>  
 [<span data-ttu-id="d7f68-122">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="d7f68-122">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="d7f68-123">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="d7f68-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
