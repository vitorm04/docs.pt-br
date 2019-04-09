---
title: Criando tipos (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 53aa7fcc82a476c8b8bd87b059e08bee6741c0d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073774"
---
# <a name="constructing-types-entity-sql"></a><span data-ttu-id="6d92b-102">Criando tipos (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6d92b-102">Constructing Types (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="6d92b-103">fornece três tipos dos construtores: construtores, nomeados construtores de tipo e construtores de coleção de linhas.</span><span class="sxs-lookup"><span data-stu-id="6d92b-103">provides three kinds of constructors: row constructors, named type constructors, and collection constructors.</span></span>  
  
## <a name="row-constructors"></a><span data-ttu-id="6d92b-104">Coloque construtores</span><span class="sxs-lookup"><span data-stu-id="6d92b-104">Row Constructors</span></span>  
 <span data-ttu-id="6d92b-105">Você usa construtores de linha em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] para construir registros anônimos, tipados estrutural de um ou mais valores.</span><span class="sxs-lookup"><span data-stu-id="6d92b-105">You use row constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="6d92b-106">O tipo do resultado de um construtor de linha é um tipo de linha cujos tipos de campo correspondem aos tipos de valores usados para construir a linha.</span><span class="sxs-lookup"><span data-stu-id="6d92b-106">The result type of a row constructor is a row type whose field types correspond to the types of the values used to construct the row.</span></span> <span data-ttu-id="6d92b-107">Por exemplo, a expressão a seguir constrói um valor do tipo `Record(a int, b string, c int)`:</span><span class="sxs-lookup"><span data-stu-id="6d92b-107">For example, the following expression constructs a value of type `Record(a int, b string, c int)`:</span></span>  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 <span data-ttu-id="6d92b-108">Se você não fornecer um alias para um construtor de expressão em seguida, Entity Framework tentará gerar um.</span><span class="sxs-lookup"><span data-stu-id="6d92b-108">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="6d92b-109">Para obter mais informações, consulte a seção "Regras Serrilha" [identificadores](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="6d92b-109">For more information, see the "Aliasing Rules" section in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="6d92b-110">As seguintes regras se aplicam para o construtor de serrilha de expressão em uma linha:</span><span class="sxs-lookup"><span data-stu-id="6d92b-110">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
-   <span data-ttu-id="6d92b-111">O construtor das expressões em uma linha não pode referenciar outras alias no mesmo construtor.</span><span class="sxs-lookup"><span data-stu-id="6d92b-111">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
-   <span data-ttu-id="6d92b-112">Duas expressões no mesmo construtor de linha não podem ter as mesmas alias.</span><span class="sxs-lookup"><span data-stu-id="6d92b-112">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="6d92b-113">Para obter mais informações sobre construtores de linha, consulte [linha](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="6d92b-113">For more information about row constructors, see [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span></span>  
  
## <a name="collection-constructors"></a><span data-ttu-id="6d92b-114">Construtores de coleção</span><span class="sxs-lookup"><span data-stu-id="6d92b-114">Collection Constructors</span></span>  
 <span data-ttu-id="6d92b-115">Você usa construtores de coleção em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] para criar uma instância de um multiset de uma lista de valores.</span><span class="sxs-lookup"><span data-stu-id="6d92b-115">You use collection constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="6d92b-116">Todos os valores no construtor deve ser do tipo correspondente mutuamente `T`, e o construtor gerenciar uma coleção do tipo `Multiset<T>`.</span><span class="sxs-lookup"><span data-stu-id="6d92b-116">All the values in the constructor must be of mutually compatible type `T`, and the constructor produces a collection of type `Multiset<T>`.</span></span> <span data-ttu-id="6d92b-117">Por exemplo, a expressão a seguir cria uma coleção de inteiros:</span><span class="sxs-lookup"><span data-stu-id="6d92b-117">For example, the following expression creates a collection of integers:</span></span>  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 <span data-ttu-id="6d92b-118">Não são permitidos construtores vazios de multiset porque o tipo dos elementos não pode ser determinado.</span><span class="sxs-lookup"><span data-stu-id="6d92b-118">Empty multiset constructors are not allowed because the type of the elements cannot be determined.</span></span> <span data-ttu-id="6d92b-119">O seguinte é válido:</span><span class="sxs-lookup"><span data-stu-id="6d92b-119">The following is not valid:</span></span>  
  
 `multiset() {}`  
  
 <span data-ttu-id="6d92b-120">Para obter mais informações, consulte [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="6d92b-120">For more information, see [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md).</span></span>  
  
## <a name="named-type-constructors-namedtype-initializers"></a><span data-ttu-id="6d92b-121">Construtores nomes de tipo (inicializadores de NamedType)</span><span class="sxs-lookup"><span data-stu-id="6d92b-121">Named Type Constructors (NamedType Initializers)</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="6d92b-122">permite que os construtores de tipo (inicializadores) criar instâncias de tipos complexos nomeados e tipos de entidade.</span><span class="sxs-lookup"><span data-stu-id="6d92b-122">allows type constructors (initializers) to create instances of named complex types and entity types.</span></span> <span data-ttu-id="6d92b-123">Por exemplo, a expressão a seguir cria uma instância de um tipo de `Person` .</span><span class="sxs-lookup"><span data-stu-id="6d92b-123">For example, the following expression creates an instance of a `Person` type.</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="6d92b-124">A expressão a seguir cria uma instância de um tipo complexo.</span><span class="sxs-lookup"><span data-stu-id="6d92b-124">The following expression creates an instance of a complex type.</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="6d92b-125">A expressão a seguir cria uma instância de um tipo complexo aninhado.</span><span class="sxs-lookup"><span data-stu-id="6d92b-125">The following expression creates an instance of a nested complex type.</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="6d92b-126">A expressão a seguir cria uma instância de um objeto com um tipo complexo aninhado.</span><span class="sxs-lookup"><span data-stu-id="6d92b-126">The following expression creates an instance of an entity with a nested complex type.</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="6d92b-127">O exemplo a seguir mostra como inicializar uma propriedade de um tipo complexo para nulo.</span><span class="sxs-lookup"><span data-stu-id="6d92b-127">The following example shows how to initialize a property of a complex type to null.</span></span> `MyModel.ZipCode(‘98118’, null)`  
  
 <span data-ttu-id="6d92b-128">Os argumentos para o construtor são considerados para estar na mesma ordem que a declaração de atributos de tipo.</span><span class="sxs-lookup"><span data-stu-id="6d92b-128">The arguments to the constructor are assumed to be in the same order as the declaration of the attributes of the type.</span></span>  
  
 <span data-ttu-id="6d92b-129">Para obter mais informações, consulte [construtor de tipo nomeado](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="6d92b-129">For more information, see [Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d92b-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d92b-130">See also</span></span>

- [<span data-ttu-id="6d92b-131">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6d92b-131">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="6d92b-132">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6d92b-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="6d92b-133">Sistema de tipos</span><span class="sxs-lookup"><span data-stu-id="6d92b-133">Type System</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)
