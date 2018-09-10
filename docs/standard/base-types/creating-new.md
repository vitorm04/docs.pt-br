---
title: Criação de novas cadeias de caracteres no .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET Framework], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 477791a0d62186b6cb88d0fae3aa9b4e38b3ef35
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43870104"
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="c8d28-102">Criação de novas cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="c8d28-102">Creating New Strings in .NET</span></span>
<span data-ttu-id="c8d28-103">O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] permite que cadeias de caracteres sejam criadas usando uma atribuição simples e também sobrecarrega um constructo de classe para dar suporte à criação de cadeias de caracteres usando um número de parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="c8d28-103">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="c8d28-104">O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] também fornece vários métodos na classe <xref:System.String?displayProperty=nameWithType> que criam novos objetos de cadeia de caracteres combinando várias cadeias de caracteres, matrizes de cadeias de caracteres ou objetos.</span><span class="sxs-lookup"><span data-stu-id="c8d28-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="c8d28-105">Criando cadeias de caracteres usando atribuição</span><span class="sxs-lookup"><span data-stu-id="c8d28-105">Creating Strings Using Assignment</span></span>  
 <span data-ttu-id="c8d28-106">A maneira mais fácil para criar um novo objeto <xref:System.String> é simplesmente atribuir uma cadeia de caracteres literal a um objeto <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c8d28-106">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="c8d28-107">Criando cadeias de caracteres usando um construtor de classe</span><span class="sxs-lookup"><span data-stu-id="c8d28-107">Creating Strings Using a Class Constructor</span></span>  
 <span data-ttu-id="c8d28-108">Você pode usar sobrecargas do constructo de classe <xref:System.String> para criar cadeias de caracteres de matrizes de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c8d28-108">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="c8d28-109">Você também pode criar uma nova cadeia de caracteres duplicando um caractere específico, m número de vezes especificado.</span><span class="sxs-lookup"><span data-stu-id="c8d28-109">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="c8d28-110">Métodos que retornam cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="c8d28-110">Methods that Return Strings</span></span>  
 <span data-ttu-id="c8d28-111">A tabela a seguir lista vários métodos úteis que retornam novos objetos de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c8d28-111">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="c8d28-112">Nome do método</span><span class="sxs-lookup"><span data-stu-id="c8d28-112">Method name</span></span>|<span data-ttu-id="c8d28-113">Use</span><span class="sxs-lookup"><span data-stu-id="c8d28-113">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="c8d28-114">Cria uma cadeia de caracteres formatada de um conjunto de objetos de entrada.</span><span class="sxs-lookup"><span data-stu-id="c8d28-114">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="c8d28-115">Cria cadeias de caracteres de duas ou mais cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c8d28-115">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="c8d28-116">Cria uma nova cadeia de caracteres combinando uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c8d28-116">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="c8d28-117">Cria uma nova cadeia de caracteres inserindo uma cadeia de caracteres no índice especificado de uma cadeia de caracteres existente.</span><span class="sxs-lookup"><span data-stu-id="c8d28-117">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="c8d28-118">Copia caracteres especificados de uma cadeia de caracteres para uma posição especificada em uma matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c8d28-118">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="c8d28-119">Formatar</span><span class="sxs-lookup"><span data-stu-id="c8d28-119">Format</span></span>  
 <span data-ttu-id="c8d28-120">Você pode usar o método **String.Format** para criar cadeias de caracteres formatadas e concatenar cadeias de caracteres que representam vários objetos.</span><span class="sxs-lookup"><span data-stu-id="c8d28-120">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="c8d28-121">Este método converte automaticamente qualquer objeto passado em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c8d28-121">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="c8d28-122">Por exemplo, se seu aplicativo precisar exibir um valor **Int32** e um valor **DateTime** para o usuário, você pode facilmente criar uma cadeia de caracteres para representar esses valores usando o método **Format**.</span><span class="sxs-lookup"><span data-stu-id="c8d28-122">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="c8d28-123">Para obter informações sobre as convenções de formatação usadas com esse método, consulte a seção sobre [formatação de composição](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="c8d28-123">For information about formatting conventions used with this method, see the section on [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="c8d28-124">O exemplo a seguir usa o método **Format** para criar uma cadeia de caracteres que usa uma variável de inteiro.</span><span class="sxs-lookup"><span data-stu-id="c8d28-124">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="c8d28-125">Neste exemplo, <xref:System.DateTime.Now%2A?displayProperty=nameWithType> exibe a data e hora atuais da maneira especificada pela cultura associada ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="c8d28-125">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="c8d28-126">Concat</span><span class="sxs-lookup"><span data-stu-id="c8d28-126">Concat</span></span>  
 <span data-ttu-id="c8d28-127">O método **String.Concat** pode ser usado para criar facilmente um novo objeto de cadeia de caracteres de dois ou mais objetos existentes.</span><span class="sxs-lookup"><span data-stu-id="c8d28-127">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="c8d28-128">Ele fornece uma maneira independente da linguagem para concatenar cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c8d28-128">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="c8d28-129">Este método aceita qualquer classe derivada de **System.Object**.</span><span class="sxs-lookup"><span data-stu-id="c8d28-129">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="c8d28-130">O exemplo a seguir cria uma cadeia de caracteres de dois objetos de cadeia de caracteres existentes e um caractere de separação.</span><span class="sxs-lookup"><span data-stu-id="c8d28-130">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="c8d28-131">Join</span><span class="sxs-lookup"><span data-stu-id="c8d28-131">Join</span></span>  
 <span data-ttu-id="c8d28-132">O método **String.Join** cria uma nova cadeia de caracteres a partir de uma matriz de cadeias de caracteres e uma cadeia de caracteres de separador.</span><span class="sxs-lookup"><span data-stu-id="c8d28-132">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="c8d28-133">Esse método é útil se você quiser concatenar várias cadeias de caracteres fazendo uma lista, talvez separada por vírgula.</span><span class="sxs-lookup"><span data-stu-id="c8d28-133">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="c8d28-134">O exemplo a seguir usa um espaço para associar uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c8d28-134">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="c8d28-135">Inserir</span><span class="sxs-lookup"><span data-stu-id="c8d28-135">Insert</span></span>  
 <span data-ttu-id="c8d28-136">O método **String.Insert** cria uma nova cadeia de caracteres inserindo uma cadeia de caracteres em uma posição especificada em outra cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c8d28-136">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="c8d28-137">Este método usa um índice baseado em zero.</span><span class="sxs-lookup"><span data-stu-id="c8d28-137">This method uses a zero-based index.</span></span> <span data-ttu-id="c8d28-138">O exemplo a seguir insere uma cadeia de caracteres na quinta posição do índice de `MyString` e cria uma nova cadeia de caracteres com esse valor.</span><span class="sxs-lookup"><span data-stu-id="c8d28-138">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="c8d28-139">CopyTo</span><span class="sxs-lookup"><span data-stu-id="c8d28-139">CopyTo</span></span>  
 <span data-ttu-id="c8d28-140">O método **String.CopyTo** copia partes de uma cadeia de caracteres em uma matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c8d28-140">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="c8d28-141">Você pode especificar o índice inicial da cadeia de caracteres e o número de caracteres a serem copiados.</span><span class="sxs-lookup"><span data-stu-id="c8d28-141">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="c8d28-142">Este método usa o índice de origem, uma matriz de caracteres, o índice de destino e o número de caracteres a serem copiados.</span><span class="sxs-lookup"><span data-stu-id="c8d28-142">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="c8d28-143">Todos os índices são baseados em zero.</span><span class="sxs-lookup"><span data-stu-id="c8d28-143">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="c8d28-144">O exemplo a seguir usa o método **CopyTo** para copiar os caracteres da palavra "Hello" de um objeto de cadeia de caracteres para a primeira posição de índice de uma matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c8d28-144">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="c8d28-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8d28-145">See also</span></span>

- [<span data-ttu-id="c8d28-146">Operações básicas de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="c8d28-146">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)  
- [<span data-ttu-id="c8d28-147">Formatação de composição</span><span class="sxs-lookup"><span data-stu-id="c8d28-147">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
