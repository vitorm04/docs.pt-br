---
title: Convenções de maiusculas e minúsculas
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 070fc69728c2cb38e465dab9f6f591a77a857531
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44274250"
---
# <a name="capitalization-conventions"></a><span data-ttu-id="69a99-102">Convenções de maiusculas e minúsculas</span><span class="sxs-lookup"><span data-stu-id="69a99-102">Capitalization Conventions</span></span>
<span data-ttu-id="69a99-103">As diretrizes neste capítulo dispor de um método simples para usar o caso, que, quando aplicadas de forma consistente, os identificadores de marca para tipos, membros e parâmetros de fácil leitura.</span><span class="sxs-lookup"><span data-stu-id="69a99-103">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>  
  
## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="69a99-104">Regras de maiusculas e minúsculas de identificadores</span><span class="sxs-lookup"><span data-stu-id="69a99-104">Capitalization Rules for Identifiers</span></span>  
 <span data-ttu-id="69a99-105">Para diferenciar as palavras em um identificador, maiuscula a primeira letra de cada palavra no identificador.</span><span class="sxs-lookup"><span data-stu-id="69a99-105">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="69a99-106">Não use sublinhados para diferenciar as palavras, ou, de fato, em qualquer lugar em identificadores.</span><span class="sxs-lookup"><span data-stu-id="69a99-106">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="69a99-107">Há duas maneiras de apropriado para capitalizar identificadores, dependendo do uso do identificador:</span><span class="sxs-lookup"><span data-stu-id="69a99-107">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>  
  
-   <span data-ttu-id="69a99-108">PascalCasing</span><span class="sxs-lookup"><span data-stu-id="69a99-108">PascalCasing</span></span>  
  
-   <span data-ttu-id="69a99-109">camelCasing</span><span class="sxs-lookup"><span data-stu-id="69a99-109">camelCasing</span></span>  
  
 <span data-ttu-id="69a99-110">A convenção de PascalCasing, usada para todos os identificadores, exceto os nomes de parâmetro, escreve o primeiro caractere de cada palavra (incluindo acrônimos ao longo de duas letras), conforme mostrado nos exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="69a99-110">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 <span data-ttu-id="69a99-111">Um caso especial é feito para as abreviações de duas letras em que as duas letras estão em maiusculas, de conforme mostrado na seguinte identificador:</span><span class="sxs-lookup"><span data-stu-id="69a99-111">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>  
  
 `IOStream`  
  
 <span data-ttu-id="69a99-112">A convenção de camelCasing, usada somente para os nomes de parâmetro, escreve o primeiro caractere de cada palavra, exceto a primeira palavra, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="69a99-112">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="69a99-113">Como o exemplo também mostra, acrônimos de duas letras que começam a um identificador em camel case estão em minúsculas.</span><span class="sxs-lookup"><span data-stu-id="69a99-113">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 <span data-ttu-id="69a99-114">**✓ DO** usar PascalCasing para todos os membros, tipo e namespace nomes públicos consiste em várias palavras.</span><span class="sxs-lookup"><span data-stu-id="69a99-114">**✓ DO** use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>  
  
 <span data-ttu-id="69a99-115">**✓ DO** usar camelCasing para nomes de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="69a99-115">**✓ DO** use camelCasing for parameter names.</span></span>  
  
 <span data-ttu-id="69a99-116">A tabela a seguir descreve as regras de maiusculas e minúsculas para diferentes tipos de identificadores.</span><span class="sxs-lookup"><span data-stu-id="69a99-116">The following table describes the capitalization rules for different types of identifiers.</span></span>  
  
|<span data-ttu-id="69a99-117">Identificador</span><span class="sxs-lookup"><span data-stu-id="69a99-117">Identifier</span></span>|<span data-ttu-id="69a99-118">Maiúsculas</span><span class="sxs-lookup"><span data-stu-id="69a99-118">Casing</span></span>|<span data-ttu-id="69a99-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69a99-119">Example</span></span>|  
|----------------|------------|-------------|  
|<span data-ttu-id="69a99-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="69a99-120">Namespace</span></span>|<span data-ttu-id="69a99-121">Pascal</span><span class="sxs-lookup"><span data-stu-id="69a99-121">Pascal</span></span>|`namespace System.Security { ... }`|  
|<span data-ttu-id="69a99-122">Tipo</span><span class="sxs-lookup"><span data-stu-id="69a99-122">Type</span></span>|<span data-ttu-id="69a99-123">Pascal</span><span class="sxs-lookup"><span data-stu-id="69a99-123">Pascal</span></span>|`public class StreamReader { ... }`|  
|<span data-ttu-id="69a99-124">Interface</span><span class="sxs-lookup"><span data-stu-id="69a99-124">Interface</span></span>|<span data-ttu-id="69a99-125">Pascal</span><span class="sxs-lookup"><span data-stu-id="69a99-125">Pascal</span></span>|`public interface IEnumerable { ... }`|  
|<span data-ttu-id="69a99-126">Método</span><span class="sxs-lookup"><span data-stu-id="69a99-126">Method</span></span>|<span data-ttu-id="69a99-127">Pascal</span><span class="sxs-lookup"><span data-stu-id="69a99-127">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|<span data-ttu-id="69a99-128">Propriedade</span><span class="sxs-lookup"><span data-stu-id="69a99-128">Property</span></span>|<span data-ttu-id="69a99-129">Pascal</span><span class="sxs-lookup"><span data-stu-id="69a99-129">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|<span data-ttu-id="69a99-130">evento</span><span class="sxs-lookup"><span data-stu-id="69a99-130">Event</span></span>|<span data-ttu-id="69a99-131">Pascal</span><span class="sxs-lookup"><span data-stu-id="69a99-131">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|<span data-ttu-id="69a99-132">Campo</span><span class="sxs-lookup"><span data-stu-id="69a99-132">Field</span></span>|<span data-ttu-id="69a99-133">Pascal</span><span class="sxs-lookup"><span data-stu-id="69a99-133">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|<span data-ttu-id="69a99-134">Valor de enumeração</span><span class="sxs-lookup"><span data-stu-id="69a99-134">Enum value</span></span>|<span data-ttu-id="69a99-135">Pascal</span><span class="sxs-lookup"><span data-stu-id="69a99-135">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|<span data-ttu-id="69a99-136">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="69a99-136">Parameter</span></span>|<span data-ttu-id="69a99-137">Camel</span><span class="sxs-lookup"><span data-stu-id="69a99-137">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="69a99-138">Aproveitando a palavras compostas e termos comuns</span><span class="sxs-lookup"><span data-stu-id="69a99-138">Capitalizing Compound Words and Common Terms</span></span>  
 <span data-ttu-id="69a99-139">A maioria dos termos compostos são tratados como palavras individuais para fins de maiusculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="69a99-139">Most compound terms are treated as single words for purposes of capitalization.</span></span>  
  
 <span data-ttu-id="69a99-140">**X DO NOT** cada palavra em palavras compostas de forma fechada chamadas em maiuscula.</span><span class="sxs-lookup"><span data-stu-id="69a99-140">**X DO NOT** capitalize each word in so-called closed-form compound words.</span></span>  
  
 <span data-ttu-id="69a99-141">Essas são as palavras compostas escritas como uma única palavra, como o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="69a99-141">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="69a99-142">Para fins de diretrizes de maiusculas e minúsculas, trate uma palavra composta do formulário fechado como uma única palavra.</span><span class="sxs-lookup"><span data-stu-id="69a99-142">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="69a99-143">Use um dicionário atual para determinar se uma palavra composta é escrita em forma fechada.</span><span class="sxs-lookup"><span data-stu-id="69a99-143">Use a current dictionary to determine if a compound word is written in closed form.</span></span>  
  
|<span data-ttu-id="69a99-144">Pascal</span><span class="sxs-lookup"><span data-stu-id="69a99-144">Pascal</span></span>|<span data-ttu-id="69a99-145">Camel</span><span class="sxs-lookup"><span data-stu-id="69a99-145">Camel</span></span>|<span data-ttu-id="69a99-146">não</span><span class="sxs-lookup"><span data-stu-id="69a99-146">Not</span></span>|  
|------------|-----------|---------|  
|`BitFlag`|`bitFlag`|`Bitflag`|  
|`Callback`|`callback`|`CallBack`|  
|`Canceled`|`canceled`|`Cancelled`|  
|`DoNot`|`doNot`|`Don't`|  
|`Email`|`email`|`EMail`|  
|`Endpoint`|`endpoint`|`EndPoint`|  
|`FileName`|`fileName`|`Filename`|  
|`Gridline`|`gridline`|`GridLine`|  
|`Hashtable`|`hashtable`|`HashTable`|  
|`Id`|`id`|`ID`|  
|`Indexes`|`indexes`|`Indices`|  
|`LogOff`|`logOff`|`LogOut`|  
|`LogOn`|`logOn`|`LogIn`|  
|`Metadata`|`metadata`|`MetaData, metaData`|  
|`Multipanel`|`multipanel`|`MultiPanel`|  
|`Multiview`|`multiview`|`MultiView`|  
|`Namespace`|`namespace`|`NameSpace`|  
|`Ok`|`ok`|`OK`|  
|`Pi`|`pi`|`PI`|  
|`Placeholder`|`placeholder`|`PlaceHolder`|  
|`SignIn`|`signIn`|`SignOn`|  
|`SignOut`|`signOut`|`SignOff`|  
|`UserName`|`userName`|`Username`|  
|`WhiteSpace`|`whiteSpace`|`Whitespace`|  
|`Writable`|`writable`|`Writeable`|  
  
## <a name="case-sensitivity"></a><span data-ttu-id="69a99-147">Diferenciação de maiúsculas e minúsculas</span><span class="sxs-lookup"><span data-stu-id="69a99-147">Case Sensitivity</span></span>  
 <span data-ttu-id="69a99-148">Idiomas que podem ser executados no CLR não são necessários para dar suporte a diferenciação de maiusculas e minúsculas, embora alguns façam.</span><span class="sxs-lookup"><span data-stu-id="69a99-148">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="69a99-149">Mesmo se a linguagem dá suporte a ele, outras linguagens que podem acessar sua estrutura, não.</span><span class="sxs-lookup"><span data-stu-id="69a99-149">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="69a99-150">Todas as APIs sejam acessíveis externamente, portanto, não podem contar caso sozinho para distinguir entre os dois nomes no mesmo contexto.</span><span class="sxs-lookup"><span data-stu-id="69a99-150">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>  
  
 <span data-ttu-id="69a99-151">**X DO NOT** suponha que todas as linguagens de programação diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="69a99-151">**X DO NOT** assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="69a99-152">Eles não são.</span><span class="sxs-lookup"><span data-stu-id="69a99-152">They are not.</span></span> <span data-ttu-id="69a99-153">Nomes não podem diferir por caso sozinho.</span><span class="sxs-lookup"><span data-stu-id="69a99-153">Names cannot differ by case alone.</span></span>  
  
 <span data-ttu-id="69a99-154">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="69a99-154">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="69a99-155">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="69a99-155">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69a99-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69a99-156">See also</span></span>

- [<span data-ttu-id="69a99-157">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="69a99-157">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="69a99-158">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="69a99-158">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
