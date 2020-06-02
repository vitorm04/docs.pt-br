---
title: Convenções de maiúsculas e minúsculas
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
ms.openlocfilehash: 10d628700a9cbf0e842416878ec2c7febfa3d6f5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280394"
---
# <a name="capitalization-conventions"></a><span data-ttu-id="8de33-102">Convenções de maiúsculas e minúsculas</span><span class="sxs-lookup"><span data-stu-id="8de33-102">Capitalization Conventions</span></span>
<span data-ttu-id="8de33-103">As diretrizes neste capítulo destacam um método simples para usar o caso, quando aplicado de forma consistente, tornar os identificadores para tipos, membros e parâmetros fáceis de ler.</span><span class="sxs-lookup"><span data-stu-id="8de33-103">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>

## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="8de33-104">Regras de capitalização para identificadores</span><span class="sxs-lookup"><span data-stu-id="8de33-104">Capitalization Rules for Identifiers</span></span>
 <span data-ttu-id="8de33-105">Para diferenciar palavras em um identificador, coloque em maiúscula a primeira letra de cada palavra no identificador.</span><span class="sxs-lookup"><span data-stu-id="8de33-105">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="8de33-106">Não use sublinhados para diferenciar palavras, ou para esse assunto, em qualquer lugar nos identificadores.</span><span class="sxs-lookup"><span data-stu-id="8de33-106">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="8de33-107">Há duas maneiras apropriadas de colocar identificadores em maiúsculas, dependendo do uso do identificador:</span><span class="sxs-lookup"><span data-stu-id="8de33-107">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>

- <span data-ttu-id="8de33-108">PascalCasing</span><span class="sxs-lookup"><span data-stu-id="8de33-108">PascalCasing</span></span>

- <span data-ttu-id="8de33-109">camelCasing</span><span class="sxs-lookup"><span data-stu-id="8de33-109">camelCasing</span></span>

 <span data-ttu-id="8de33-110">A Convenção PascalCasing, usada para todos os identificadores, exceto nomes de parâmetro, coloca em maiúscula o primeiro caractere de cada palavra (incluindo acrônimos sobre duas letras de comprimento), conforme mostrado nos exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="8de33-110">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>

 `PropertyDescriptor`
 `HtmlTag`

 <span data-ttu-id="8de33-111">Um caso especial é feito para acrônimos de duas letras nas quais as letras são colocadas em maiúsculas, conforme mostrado no identificador a seguir:</span><span class="sxs-lookup"><span data-stu-id="8de33-111">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>

 `IOStream`

 <span data-ttu-id="8de33-112">A Convenção camelCasing, usada apenas para nomes de parâmetro, coloca em maiúscula o primeiro caractere de cada palavra, exceto a primeira palavra, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="8de33-112">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="8de33-113">Como o exemplo também mostra, os acrônimos de duas letras que começam um identificador de camel-case são minúsculos.</span><span class="sxs-lookup"><span data-stu-id="8de33-113">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>

 `propertyDescriptor`
 `ioStream`
 `htmlTag`

 <span data-ttu-id="8de33-114">✔️ Use PascalCasing para todos os nomes de membro público, tipo e namespace que consistem em várias palavras.</span><span class="sxs-lookup"><span data-stu-id="8de33-114">✔️ DO use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>

 <span data-ttu-id="8de33-115">✔️ Use camelCasing para nomes de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8de33-115">✔️ DO use camelCasing for parameter names.</span></span>

 <span data-ttu-id="8de33-116">A tabela a seguir descreve as regras de capitalização para diferentes tipos de identificadores.</span><span class="sxs-lookup"><span data-stu-id="8de33-116">The following table describes the capitalization rules for different types of identifiers.</span></span>

|<span data-ttu-id="8de33-117">Identificador</span><span class="sxs-lookup"><span data-stu-id="8de33-117">Identifier</span></span>|<span data-ttu-id="8de33-118">Capitalização</span><span class="sxs-lookup"><span data-stu-id="8de33-118">Casing</span></span>|<span data-ttu-id="8de33-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8de33-119">Example</span></span>|
|----------------|------------|-------------|
|<span data-ttu-id="8de33-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="8de33-120">Namespace</span></span>|<span data-ttu-id="8de33-121">Pascal</span><span class="sxs-lookup"><span data-stu-id="8de33-121">Pascal</span></span>|`namespace System.Security { ... }`|
|<span data-ttu-id="8de33-122">Tipo</span><span class="sxs-lookup"><span data-stu-id="8de33-122">Type</span></span>|<span data-ttu-id="8de33-123">Pascal</span><span class="sxs-lookup"><span data-stu-id="8de33-123">Pascal</span></span>|`public class StreamReader { ... }`|
|<span data-ttu-id="8de33-124">Interface</span><span class="sxs-lookup"><span data-stu-id="8de33-124">Interface</span></span>|<span data-ttu-id="8de33-125">Pascal</span><span class="sxs-lookup"><span data-stu-id="8de33-125">Pascal</span></span>|`public interface IEnumerable { ... }`|
|<span data-ttu-id="8de33-126">Método</span><span class="sxs-lookup"><span data-stu-id="8de33-126">Method</span></span>|<span data-ttu-id="8de33-127">Pascal</span><span class="sxs-lookup"><span data-stu-id="8de33-127">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|
|<span data-ttu-id="8de33-128">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8de33-128">Property</span></span>|<span data-ttu-id="8de33-129">Pascal</span><span class="sxs-lookup"><span data-stu-id="8de33-129">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|
|<span data-ttu-id="8de33-130">Evento</span><span class="sxs-lookup"><span data-stu-id="8de33-130">Event</span></span>|<span data-ttu-id="8de33-131">Pascal</span><span class="sxs-lookup"><span data-stu-id="8de33-131">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|
|<span data-ttu-id="8de33-132">Campo</span><span class="sxs-lookup"><span data-stu-id="8de33-132">Field</span></span>|<span data-ttu-id="8de33-133">Pascal</span><span class="sxs-lookup"><span data-stu-id="8de33-133">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|
|<span data-ttu-id="8de33-134">Valor de enumeração</span><span class="sxs-lookup"><span data-stu-id="8de33-134">Enum value</span></span>|<span data-ttu-id="8de33-135">Pascal</span><span class="sxs-lookup"><span data-stu-id="8de33-135">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|
|<span data-ttu-id="8de33-136">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="8de33-136">Parameter</span></span>|<span data-ttu-id="8de33-137">Camel</span><span class="sxs-lookup"><span data-stu-id="8de33-137">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|

## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="8de33-138">Capitalização de palavras compostas e termos comuns</span><span class="sxs-lookup"><span data-stu-id="8de33-138">Capitalizing Compound Words and Common Terms</span></span>
 <span data-ttu-id="8de33-139">A maioria dos termos compostos é tratada como palavras únicas para fins de capitalização.</span><span class="sxs-lookup"><span data-stu-id="8de33-139">Most compound terms are treated as single words for purposes of capitalization.</span></span>

 <span data-ttu-id="8de33-140">❌Não coloque todas as palavras em maiúsculas nas chamadas de palavras compostas de forma fechada.</span><span class="sxs-lookup"><span data-stu-id="8de33-140">❌ DO NOT capitalize each word in so-called closed-form compound words.</span></span>

 <span data-ttu-id="8de33-141">Essas são palavras compostas escritas como uma única palavra, como ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="8de33-141">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="8de33-142">Para as diretrizes de uso de maiúsculas e minúsculas, trate uma palavra composta de forma fechada como uma única palavra.</span><span class="sxs-lookup"><span data-stu-id="8de33-142">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="8de33-143">Use um dicionário atual para determinar se uma palavra composta é escrita em formato fechado.</span><span class="sxs-lookup"><span data-stu-id="8de33-143">Use a current dictionary to determine if a compound word is written in closed form.</span></span>

|<span data-ttu-id="8de33-144">Pascal</span><span class="sxs-lookup"><span data-stu-id="8de33-144">Pascal</span></span>|<span data-ttu-id="8de33-145">Camel</span><span class="sxs-lookup"><span data-stu-id="8de33-145">Camel</span></span>|<span data-ttu-id="8de33-146">Not</span><span class="sxs-lookup"><span data-stu-id="8de33-146">Not</span></span>|
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

## <a name="case-sensitivity"></a><span data-ttu-id="8de33-147">Diferenciação de maiúsculas e minúsculas</span><span class="sxs-lookup"><span data-stu-id="8de33-147">Case Sensitivity</span></span>
 <span data-ttu-id="8de33-148">Os idiomas que podem ser executados no CLR não precisam dar suporte à diferenciação de maiúsculas e minúsculas, embora alguns façam.</span><span class="sxs-lookup"><span data-stu-id="8de33-148">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="8de33-149">Mesmo que seu idioma dê suporte a isso, outras linguagens que podem acessar sua estrutura não têm.</span><span class="sxs-lookup"><span data-stu-id="8de33-149">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="8de33-150">As APIs que são acessíveis externamente, portanto, não podem depender apenas de maiúsculas e minúsculas para distinguir entre dois nomes no mesmo contexto.</span><span class="sxs-lookup"><span data-stu-id="8de33-150">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>

 <span data-ttu-id="8de33-151">❌Não presuma que todas as linguagens de programação diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="8de33-151">❌ DO NOT assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="8de33-152">Eles não são.</span><span class="sxs-lookup"><span data-stu-id="8de33-152">They are not.</span></span> <span data-ttu-id="8de33-153">Os nomes não podem diferir apenas por maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="8de33-153">Names cannot differ by case alone.</span></span>

 <span data-ttu-id="8de33-154">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="8de33-154">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="8de33-155">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="8de33-155">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="8de33-156">Veja também</span><span class="sxs-lookup"><span data-stu-id="8de33-156">See also</span></span>

- [<span data-ttu-id="8de33-157">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="8de33-157">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="8de33-158">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="8de33-158">Naming Guidelines</span></span>](naming-guidelines.md)
