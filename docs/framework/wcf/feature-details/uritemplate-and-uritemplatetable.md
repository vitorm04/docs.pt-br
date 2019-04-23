---
title: UriTemplate and UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: b0dc3b2b747bc08da239490db7db3ba77d1e7ed8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130241"
---
# <a name="uritemplate-and-uritemplatetable"></a><span data-ttu-id="2ff7d-102">UriTemplate and UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="2ff7d-102">UriTemplate and UriTemplateTable</span></span>
<span data-ttu-id="2ff7d-103">Os desenvolvedores da Web exigem a capacidade para descrever a forma e o layout dos URIs que seus serviços respondem a.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-103">Web developers require the ability to describe the shape and layout of the URIs that their services respond to.</span></span> <span data-ttu-id="2ff7d-104">Windows Communication Foundation (WCF) adicionadas duas novas classes para dar aos desenvolvedores controle sobre seus URIs.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-104">Windows Communication Foundation (WCF) added two new classes to give developers control over their URIs.</span></span> <span data-ttu-id="2ff7d-105"><xref:System.UriTemplate> e <xref:System.UriTemplateTable> formam a base do mecanismo de expedição baseada em URI no WCF.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-105"><xref:System.UriTemplate> and <xref:System.UriTemplateTable> form the basis of the URI-based dispatch engine in WCF.</span></span> <span data-ttu-id="2ff7d-106">Essas classes também podem ser usadas em seu próprios, permitindo que os desenvolvedores tirem proveito de modelos e o URI de mecanismo de mapeamento sem implementar um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-106">These classes can also be used on their own, allowing developers to take advantage of templates and the URI mapping mechanism without implementing a WCF service.</span></span>  
  
## <a name="templates"></a><span data-ttu-id="2ff7d-107">Modelos</span><span class="sxs-lookup"><span data-stu-id="2ff7d-107">Templates</span></span>  
 <span data-ttu-id="2ff7d-108">Um modelo é uma maneira de descrever um conjunto de URIs relativos.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-108">A template is a way to describe a set of relative URIs.</span></span> <span data-ttu-id="2ff7d-109">O conjunto de modelos URI na tabela a seguir mostra como um sistema que recupera vários tipos de informações meteorológicas pode ser definido.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-109">The set of URI templates in the following table shows how a system that retrieves various types of weather information might be defined.</span></span>  
  
|<span data-ttu-id="2ff7d-110">Dados</span><span class="sxs-lookup"><span data-stu-id="2ff7d-110">Data</span></span>|<span data-ttu-id="2ff7d-111">Modelo</span><span class="sxs-lookup"><span data-stu-id="2ff7d-111">Template</span></span>|  
|----------|--------------|  
|<span data-ttu-id="2ff7d-112">Previsão nacional</span><span class="sxs-lookup"><span data-stu-id="2ff7d-112">National Forecast</span></span>|<span data-ttu-id="2ff7d-113">clima/nacional</span><span class="sxs-lookup"><span data-stu-id="2ff7d-113">weather/national</span></span>|  
|<span data-ttu-id="2ff7d-114">Previsão do estado</span><span class="sxs-lookup"><span data-stu-id="2ff7d-114">State Forecast</span></span>|<span data-ttu-id="2ff7d-115">weather/{state}</span><span class="sxs-lookup"><span data-stu-id="2ff7d-115">weather/{state}</span></span>|  
|<span data-ttu-id="2ff7d-116">Previsão de cidade</span><span class="sxs-lookup"><span data-stu-id="2ff7d-116">City Forecast</span></span>|<span data-ttu-id="2ff7d-117">weather/{state}/{city}</span><span class="sxs-lookup"><span data-stu-id="2ff7d-117">weather/{state}/{city}</span></span>|  
|<span data-ttu-id="2ff7d-118">Previsão de atividade</span><span class="sxs-lookup"><span data-stu-id="2ff7d-118">Activity Forecast</span></span>|<span data-ttu-id="2ff7d-119">weather/{state}/{city}/{activity}</span><span class="sxs-lookup"><span data-stu-id="2ff7d-119">weather/{state}/{city}/{activity}</span></span>|  
  
 <span data-ttu-id="2ff7d-120">Esta tabela descreve um conjunto de URIs estruturalmente semelhantes.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-120">This table describes a set of structurally similar URIs.</span></span> <span data-ttu-id="2ff7d-121">Cada entrada é um modelo de URI.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-121">Each entry is a URI template.</span></span> <span data-ttu-id="2ff7d-122">Os segmentos entre chaves descrevem variáveis.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-122">The segments in curly braces describe variables.</span></span> <span data-ttu-id="2ff7d-123">Os segmentos não entre chaves descrevem cadeias de caracteres literais.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-123">The segments not in curly braces describe literal strings.</span></span> <span data-ttu-id="2ff7d-124">As classes de modelo WCF permitir que os desenvolvedores utilizam um URI de entrada, por exemplo, "/ clima/wa/seattle/circulando" e fazer sua correspondência para um modelo que descreve, "/weather/ {estado} / {cidade} / {atividade}".</span><span class="sxs-lookup"><span data-stu-id="2ff7d-124">The WCF template classes allow a developer to take an incoming URI, for example, "/weather/wa/seattle/cycling", and match it to a template that describes it, "/weather/{state}/{city}/{activity}".</span></span>  
  
## <a name="uritemplate"></a><span data-ttu-id="2ff7d-125">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="2ff7d-125">UriTemplate</span></span>  
 <span data-ttu-id="2ff7d-126"><xref:System.UriTemplate> é uma classe que encapsula um modelo de URI.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-126"><xref:System.UriTemplate> is a class that encapsulates a URI template.</span></span> <span data-ttu-id="2ff7d-127">O construtor aceita um parâmetro de cadeia de caracteres que define o modelo.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-127">The constructor takes a string parameter that defines the template.</span></span> <span data-ttu-id="2ff7d-128">Essa cadeia de caracteres contém o modelo no formato descrito na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-128">This string contains the template in the format described in the next section.</span></span> <span data-ttu-id="2ff7d-129">O <xref:System.UriTemplate> classe fornece métodos que permitem que você correspondem a um URI de entrada para um modelo, gerar um URI de um modelo, recuperar uma coleção de nomes variáveis usados no modelo, determinar se dois modelos são equivalentes e retornam o modelo cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-129">The <xref:System.UriTemplate> class provides methods that allow you match an incoming URI to a template, generate a URI from a template, retrieve a collection of variable names used in the template, determine whether two templates are equivalent, and return the template's string.</span></span>  
  
 <span data-ttu-id="2ff7d-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> usa um endereço básico e um candidato URI e tenta corresponder o URI para o modelo.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> takes a base address and a candidate URI and attempts to match the URI to the template.</span></span> <span data-ttu-id="2ff7d-131">Se a correspondência for bem-sucedida, um <xref:System.UriTemplateMatch> instância será retornada.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-131">If the match is successful, a <xref:System.UriTemplateMatch> instance is returned.</span></span> <span data-ttu-id="2ff7d-132">O <xref:System.UriTemplateMatch> objeto contém um URI de base, o URI, uma coleção de nome/valor de parâmetros de consulta, uma matriz dos segmentos de caminho relativa, uma coleção de nome/valor das variáveis que foram correspondidas, candidato a <xref:System.UriTemplate> usada para executar a correspondência de instância , uma cadeia de caracteres que contém qualquer parte não correspondentes do candidato URI (usado quando o modelo tem um caractere curinga) e um objeto que está associado com o modelo.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-132">The <xref:System.UriTemplateMatch> object contains a base URI, the candidate URI, a name/value collection of the query parameters, an array of the relative path segments, a name/value collection of variables that were matched, the <xref:System.UriTemplate> instance used to perform the match, a string that contains any unmatched portion of the candidate URI (used when the template has a wildcard), and an object that is associated with the template.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ff7d-133">O <xref:System.UriTemplate> classe ignora o número da porta e o esquema durante a correspondência de um URI candidato para um modelo.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-133">The <xref:System.UriTemplate> class ignores the scheme and port number when matching a candidate URI to a template.</span></span>  
  
 <span data-ttu-id="2ff7d-134">Há dois métodos que permitem que você gerar um URI de um modelo <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> e <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-134">There are two methods that allow you to generate a URI from a template, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> and <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span></span> <span data-ttu-id="2ff7d-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> usa um endereço base e uma coleção de nome/valor de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> takes a base address and a name/value collection of parameters.</span></span> <span data-ttu-id="2ff7d-136">Esses parâmetros são substituídos por variáveis quando o modelo está associado.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-136">These parameters are substituted for variables when the template is bound.</span></span> <span data-ttu-id="2ff7d-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> usa os pares nome/valor e substitui-los da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> takes the name/value pairs and substitutes them left to right.</span></span>  
  
 <span data-ttu-id="2ff7d-138"><xref:System.UriTemplate.ToString> Retorna a cadeia de caracteres de modelo.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-138"><xref:System.UriTemplate.ToString> returns the template string.</span></span>  
  
 <span data-ttu-id="2ff7d-139">O <xref:System.UriTemplate.PathSegmentVariableNames%2A> propriedade contém uma coleção dos nomes das variáveis usadas dentro de segmentos de caminho na cadeia de caracteres de modelo.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-139">The <xref:System.UriTemplate.PathSegmentVariableNames%2A> property contains a collection of the names of the variables used within path segments in the template string.</span></span>  
  
 <span data-ttu-id="2ff7d-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> leva um <xref:System.UriTemplate> como um parâmetro e retorna um valor booliano que especifica se os dois modelos são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> takes a <xref:System.UriTemplate> as a parameter and returns a Boolean value that specifies whether the two templates are equivalent.</span></span> <span data-ttu-id="2ff7d-141">Para obter mais informações, consulte a seção de equivalência de modelo mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-141">For more information, see the Template Equivalence section later in this topic.</span></span>  
  
 <span data-ttu-id="2ff7d-142"><xref:System.UriTemplate> foi projetado para trabalhar com qualquer esquema URI que esteja de acordo com a gramática do URI do HTTP.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-142"><xref:System.UriTemplate> is designed to work with any URI scheme that conforms to the HTTP URI grammar.</span></span> <span data-ttu-id="2ff7d-143">A seguir estão exemplos de esquemas URI com suporte.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-143">The following are examples of supported URI schemes.</span></span>  
  
- <span data-ttu-id="2ff7d-144">http://</span><span class="sxs-lookup"><span data-stu-id="2ff7d-144">http://</span></span>  
  
- <span data-ttu-id="2ff7d-145">https://</span><span class="sxs-lookup"><span data-stu-id="2ff7d-145">https://</span></span>  
  
- <span data-ttu-id="2ff7d-146">net.tcp://</span><span class="sxs-lookup"><span data-stu-id="2ff7d-146">net.tcp://</span></span>  
  
- <span data-ttu-id="2ff7d-147">net.pipe://</span><span class="sxs-lookup"><span data-stu-id="2ff7d-147">net.pipe://</span></span>  
  
- <span data-ttu-id="2ff7d-148">sb://</span><span class="sxs-lookup"><span data-stu-id="2ff7d-148">sb://</span></span>  
  
 <span data-ttu-id="2ff7d-149">Esquemas como file:// e urn: / / não está em conformidade com a gramática do URI do HTTP e causar resultados imprevisíveis quando usada com modelos URI.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-149">Schemes like file:// and urn:// do not conform to the HTTP URI grammar and cause unpredictable results when used with URI templates.</span></span>  
  
### <a name="template-string-syntax"></a><span data-ttu-id="2ff7d-150">Sintaxe de cadeia de caracteres de modelo</span><span class="sxs-lookup"><span data-stu-id="2ff7d-150">Template String Syntax</span></span>  
 <span data-ttu-id="2ff7d-151">Um modelo tem três partes: um caminho, uma consulta opcional e um fragmento opcional.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-151">A template has three parts: a path, an optional query, and an optional fragment.</span></span> <span data-ttu-id="2ff7d-152">Para obter um exemplo, consulte o modelo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2ff7d-152">For an example, see the following template:</span></span>  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 <span data-ttu-id="2ff7d-153">O caminho consiste em "/weather/ {estado} / {cidade}", a consulta consiste em"? previsão = {comprimento}, e o fragmento consiste em"#frag1".</span><span class="sxs-lookup"><span data-stu-id="2ff7d-153">The path consists of "/weather/{state}/{city}", the query consists of "?forecast={length}, and the fragment consists of "#frag1".</span></span>  
  
 <span data-ttu-id="2ff7d-154">À esquerda e à direita barras "/" são opcionais na expressão de caminho.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-154">Leading and trailing slashes are optional in the path expression.</span></span> <span data-ttu-id="2ff7d-155">Expressões de consulta e de fragmento podem ser totalmente omitidas.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-155">Both the query and fragment expressions can be omitted entirely.</span></span> <span data-ttu-id="2ff7d-156">Um caminho consiste em uma série de segmentos delimitados por '/', cada segmento pode ter um valor literal, um nome de variável (escrito em {entre chaves}) ou um caractere curinga (escrito como\*').</span><span class="sxs-lookup"><span data-stu-id="2ff7d-156">A path consists of a series of segments delimited by '/', each segment can have a literal value, a variable name (written in {curly braces}), or a wildcard (written as '\*').</span></span> <span data-ttu-id="2ff7d-157">No modelo anterior a "\weather\ segmento é um literal"{city}"e o valor de"{state}"são variáveis.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-157">In the previous template the "\weather\ segment is a literal value while "{state}" and "{city}" are variables.</span></span> <span data-ttu-id="2ff7d-158">Variáveis têm seu nome do conteúdo de suas chaves e posteriormente podem ser substituídos por um valor concreto para criar uma *fechado URI*.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-158">Variables take their name from the contents of their curly braces and they can later be replaced with a concrete value to create a *closed URI*.</span></span> <span data-ttu-id="2ff7d-159">O caractere curinga é opcional, mas só pode aparecer no final do URI, onde ele corresponde logicamente "o restante do caminho".</span><span class="sxs-lookup"><span data-stu-id="2ff7d-159">The wildcard is optional, but can only appear at the end of the URI, where it logically matches "the rest of the path".</span></span>  
  
 <span data-ttu-id="2ff7d-160">A expressão de consulta, se presente, especifica uma série de pares nome/valor não ordenada delimitadas por '&'.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-160">The query expression, if present, specifies a series of unordered name/value pairs delimited by '&'.</span></span> <span data-ttu-id="2ff7d-161">Elementos da expressão de consulta podem ser literais pares (x = 2) ou um par de variáveis (x = {var}).</span><span class="sxs-lookup"><span data-stu-id="2ff7d-161">Elements of the query expression can either be literal pairs (x=2) or a variable pair (x={var}).</span></span> <span data-ttu-id="2ff7d-162">Somente o lado direito da consulta pode ter uma expressão variável.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-162">Only the right side of the query can have a variable expression.</span></span> <span data-ttu-id="2ff7d-163">({someName} = {Algumvalor} não é permitido.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-163">({someName} = {someValue} is not allowed.</span></span> <span data-ttu-id="2ff7d-164">Não emparelhado valores (? x) não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-164">Unpaired values (?x) are not permitted.</span></span> <span data-ttu-id="2ff7d-165">Não há nenhuma diferença entre uma expressão de consulta vazia e uma expressão de consulta consiste em apenas uma única '?' (ambos dizer "qualquer consulta").</span><span class="sxs-lookup"><span data-stu-id="2ff7d-165">There is no difference between an empty query expression and a query expression consisting of just a single '?' (both mean "any query").</span></span>  
  
 <span data-ttu-id="2ff7d-166">A expressão de fragmento pode consistir em um valor literal, não há variáveis são permitidas.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-166">The fragment expression can consist of a literal value, no variables are allowed.</span></span>  
  
 <span data-ttu-id="2ff7d-167">Todos os nomes de variável de modelo dentro de uma cadeia de caracteres de modelo devem ser exclusivos.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-167">All template variable names within a template string must be unique.</span></span> <span data-ttu-id="2ff7d-168">Nomes de variável de modelo diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-168">Template variable names are case-insensitive.</span></span>  
  
 <span data-ttu-id="2ff7d-169">Exemplos de cadeias de caracteres de modelo válido:</span><span class="sxs-lookup"><span data-stu-id="2ff7d-169">Examples of valid template strings:</span></span>  
  
- <span data-ttu-id="2ff7d-170">""</span><span class="sxs-lookup"><span data-stu-id="2ff7d-170">""</span></span>  
  
- <span data-ttu-id="2ff7d-171">"/ sapato"</span><span class="sxs-lookup"><span data-stu-id="2ff7d-171">"/shoe"</span></span>  
  
- <span data-ttu-id="2ff7d-172">"/shoe/\*"</span><span class="sxs-lookup"><span data-stu-id="2ff7d-172">"/shoe/\*"</span></span>  
  
- <span data-ttu-id="2ff7d-173">"{calçado} / barco"</span><span class="sxs-lookup"><span data-stu-id="2ff7d-173">"{shoe}/boat"</span></span>  
  
- <span data-ttu-id="2ff7d-174">"{calçado} / {barco} /bed/ {quilt}"</span><span class="sxs-lookup"><span data-stu-id="2ff7d-174">"{shoe}/{boat}/bed/{quilt}"</span></span>  
  
- <span data-ttu-id="2ff7d-175">"calçado / {barco}"</span><span class="sxs-lookup"><span data-stu-id="2ff7d-175">"shoe/{boat}"</span></span>  
  
- <span data-ttu-id="2ff7d-176">"calçado / {barco} /\*"</span><span class="sxs-lookup"><span data-stu-id="2ff7d-176">"shoe/{boat}/\*"</span></span>  
  
- <span data-ttu-id="2ff7d-177">"shoe/boat?x=2"</span><span class="sxs-lookup"><span data-stu-id="2ff7d-177">"shoe/boat?x=2"</span></span>  
  
- <span data-ttu-id="2ff7d-178">"shoe/{boat}?x={bed}"</span><span class="sxs-lookup"><span data-stu-id="2ff7d-178">"shoe/{boat}?x={bed}"</span></span>  
  
- <span data-ttu-id="2ff7d-179">"shoe/{boat}?x={bed}&y=band"</span><span class="sxs-lookup"><span data-stu-id="2ff7d-179">"shoe/{boat}?x={bed}&y=band"</span></span>  
  
- <span data-ttu-id="2ff7d-180">"?x={shoe}"</span><span class="sxs-lookup"><span data-stu-id="2ff7d-180">"?x={shoe}"</span></span>  
  
- <span data-ttu-id="2ff7d-181">"shoe?x=3&y={var}</span><span class="sxs-lookup"><span data-stu-id="2ff7d-181">"shoe?x=3&y={var}</span></span>  
  
 <span data-ttu-id="2ff7d-182">Exemplos de cadeias de caracteres de modelo inválido:</span><span class="sxs-lookup"><span data-stu-id="2ff7d-182">Examples of invalid template strings:</span></span>  
  
- <span data-ttu-id="2ff7d-183">"{calçado} / {CALÇADO} / x = 2" – duplicar os nomes de variáveis.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-183">"{shoe}/{SHOE}/x=2" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="2ff7d-184">"{calçado} /boat/? cama = {calçado}" – duplicar os nomes de variáveis.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-184">"{shoe}/boat/?bed={shoe}" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="2ff7d-185">"? x = x & 2 = 3" – pares nome-valor dentro de uma cadeia de caracteres de consulta devem ser exclusivos, mesmo se eles são literais.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-185">"?x=2&x=3" – Name/value pairs within a query string must be unique, even if they are literals.</span></span>  
  
- <span data-ttu-id="2ff7d-186">"? x = 2 &" – cadeia de caracteres de consulta está malformada.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-186">"?x=2&" – Query string is malformed.</span></span>  
  
- <span data-ttu-id="2ff7d-187">"? 2 & x = {calçado}" – cadeia de caracteres de consulta deve ser pares nome/valor.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-187">"?2&x={shoe}" – Query string must be name/value pairs.</span></span>  
  
- <span data-ttu-id="2ff7d-188">"? y = 2 & & X = 3" – cadeia de caracteres de consulta deve ser pares de valor de nome, nomes não podem começar com '&'.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-188">"?y=2&&X=3" – Query string must be name value pairs, names cannot start with '&'.</span></span>  
  
### <a name="compound-path-segments"></a><span data-ttu-id="2ff7d-189">Composto de segmentos de caminho</span><span class="sxs-lookup"><span data-stu-id="2ff7d-189">Compound Path Segments</span></span>  
 <span data-ttu-id="2ff7d-190">Segmentos de caminho composto permitem que um único segmento de caminho URI conter várias variáveis, bem como variáveis combinadas com literais.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-190">Compound path segments allow a single URI path segment to contain multiple variables as well as variables combined with literals.</span></span> <span data-ttu-id="2ff7d-191">A seguir estão exemplos de segmentos de caminho composto válido.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-191">The following are examples of valid compound path segments.</span></span>  
  
- <span data-ttu-id="2ff7d-192">/filename.{ext}/</span><span class="sxs-lookup"><span data-stu-id="2ff7d-192">/filename.{ext}/</span></span>  
  
- <span data-ttu-id="2ff7d-193">/{filename}.jpg/</span><span class="sxs-lookup"><span data-stu-id="2ff7d-193">/{filename}.jpg/</span></span>  
  
- <span data-ttu-id="2ff7d-194">/{filename}.{ext}/</span><span class="sxs-lookup"><span data-stu-id="2ff7d-194">/{filename}.{ext}/</span></span>  
  
- <span data-ttu-id="2ff7d-195">/{a}.{b}someLiteral{c}({d})/</span><span class="sxs-lookup"><span data-stu-id="2ff7d-195">/{a}.{b}someLiteral{c}({d})/</span></span>  
  
 <span data-ttu-id="2ff7d-196">A seguir estão exemplos de segmentos de caminho inválido.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-196">The following are examples of invalid path segments.</span></span>  
  
- <span data-ttu-id="2ff7d-197">/{} -Variáveis devem ser nomeadas.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-197">/{} - Variables must be named.</span></span>  
  
- <span data-ttu-id="2ff7d-198">/ {calçado} {barco} - variáveis devem ser separadas por um literal.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-198">/{shoe}{boat} - Variables must be separated by a literal.</span></span>  
  
### <a name="matching-and-compound-path-segments"></a><span data-ttu-id="2ff7d-199">Segmentos de caminho correspondentes e compostas</span><span class="sxs-lookup"><span data-stu-id="2ff7d-199">Matching and Compound Path Segments</span></span>  
 <span data-ttu-id="2ff7d-200">Segmentos de caminho composto permitem que você defina um UriTemplate que tem diversas variáveis dentro de um único segmento de caminho.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-200">Compound path segments allow you to define a UriTemplate that has multiple variables within a single path segment.</span></span> <span data-ttu-id="2ff7d-201">Por exemplo, na seguinte cadeia de caracteres de modelo: "Endereços / {state}. {Cidade} "duas variáveis (estado e cidade) são definidas dentro do mesmo segmento.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-201">For example, in the following template string: "Addresses/{state}.{city}" two variables (state and city) are defined within the same segment.</span></span> <span data-ttu-id="2ff7d-202">Este modelo corresponderia a uma URL como `http://example.com/Washington.Redmond` , mas também serão compatíveis com uma URL como `http://example.com/Washington.Redmond.Microsoft`.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-202">This template would match a URL such as `http://example.com/Washington.Redmond` but it will also match an URL like `http://example.com/Washington.Redmond.Microsoft`.</span></span> <span data-ttu-id="2ff7d-203">No último caso, a variável de estado conterá "Washington" e a variável de cidade irá conter "Redmond.Microsoft".</span><span class="sxs-lookup"><span data-stu-id="2ff7d-203">In the latter case, the state variable will contain "Washington" and the city variable will contain "Redmond.Microsoft".</span></span> <span data-ttu-id="2ff7d-204">Nesse caso, qualquer texto (exceto '/') corresponderá a variável {cidade}.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-204">In this case any text (except ‘/’) will match the {city} variable.</span></span> <span data-ttu-id="2ff7d-205">Se você quiser um modelo que não corresponderá o texto "extra", coloca a variável em um segmento de modelo separado, por exemplo: "Endereços / {state} / {cidade}.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-205">If you want a template that will not match the "extra" text, place the variable in a separate template segment, for example: "Addresses/{state}/{city}.</span></span>  
  
### <a name="named-wildcard-segments"></a><span data-ttu-id="2ff7d-206">Segmentos nomeados curinga</span><span class="sxs-lookup"><span data-stu-id="2ff7d-206">Named Wildcard Segments</span></span>  
 <span data-ttu-id="2ff7d-207">Um segmento curinga nomeado é qualquer segmento de caminho variável cujo nome de variável começa com o caractere curinga '\*'.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-207">A named wildcard segment is any path variable segment whose variable name begins with the wildcard character ‘\*’.</span></span> <span data-ttu-id="2ff7d-208">A seguinte cadeia de caracteres de modelo contém um segmento curinga nomeado chamado "sapato".</span><span class="sxs-lookup"><span data-stu-id="2ff7d-208">The following template string contains a named wildcard segment named "shoe".</span></span>  
  
```  
"literal/{*shoe}"  
```  
  
 <span data-ttu-id="2ff7d-209">Segmentos de curinga devem seguir as regras a seguir:</span><span class="sxs-lookup"><span data-stu-id="2ff7d-209">Wildcard segments must follow the following rules:</span></span>  
  
- <span data-ttu-id="2ff7d-210">Pode haver no máximo um segmento de curinga nomeada para cada cadeia de caracteres de modelo.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-210">There can be at most one named wildcard segment for each template string.</span></span>  
  
- <span data-ttu-id="2ff7d-211">Um segmento curinga nomeados deve aparecer no segmento mais à direita no caminho.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-211">A named wildcard segment must appear at the right-most segment in the path.</span></span>  
  
- <span data-ttu-id="2ff7d-212">Um segmento curinga nomeado não pode coexistir com um segmento curinga anônimo dentro a mesma cadeia de caracteres de modelo.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-212">A named wildcard segment cannot coexist with an anonymous wildcard segment within the same template string.</span></span>  
  
- <span data-ttu-id="2ff7d-213">O nome de um segmento curinga nomeada deve ser exclusivo.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-213">The name of a named wildcard segment must be unique.</span></span>  
  
- <span data-ttu-id="2ff7d-214">Chamado curinga segmentos não podem ter valores padrão.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-214">Named wildcard segments cannot have default values.</span></span>  
  
- <span data-ttu-id="2ff7d-215">Segmentos de curinga nomeado não podem terminar com "/".</span><span class="sxs-lookup"><span data-stu-id="2ff7d-215">Named wildcard segments cannot end with "/".</span></span>  
  
### <a name="default-variable-values"></a><span data-ttu-id="2ff7d-216">Valores de variáveis padrão</span><span class="sxs-lookup"><span data-stu-id="2ff7d-216">Default Variable Values</span></span>  
 <span data-ttu-id="2ff7d-217">Os valores de variáveis padrão permitem que você especifique valores padrão para variáveis dentro de um modelo.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-217">Default variable values allow you to specify default values for variables within a template.</span></span> <span data-ttu-id="2ff7d-218">Variáveis de padrão podem ser especificadas com as chaves que declarar a variável ou como uma coleção passada para o construtor UriTemplate.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-218">Default variables can be specified with the curly braces that declare the variable or as a collection passed to the UriTemplate constructor.</span></span> <span data-ttu-id="2ff7d-219">O modelo a seguir mostra duas maneiras para especificar um <xref:System.UriTemplate> com variáveis com valores padrão.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-219">The following template shows two ways to specify a <xref:System.UriTemplate> with variables with default values.</span></span>  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 <span data-ttu-id="2ff7d-220">Este modelo declara uma variável nomeada `a` com um valor padrão de `1` e uma variável chamada `b` com um valor padrão de `5`.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-220">This template declares a variable named `a` with a default value of `1` and a variable named `b` with a default value of `5`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ff7d-221">Somente as variáveis de segmento de caminho têm permissão para ter valores padrão.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-221">Only path segment variables are allowed to have default values.</span></span> <span data-ttu-id="2ff7d-222">Variáveis de cadeia de caracteres de consulta, as variáveis de segmento composta e variáveis nomeadas curinga não são permitidas para ter valores padrão.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-222">Query string variables, compound segment variables, and named wildcard variables are not permitted to have default values.</span></span>  
  
 <span data-ttu-id="2ff7d-223">O código a seguir mostra como os valores de variáveis padrão são tratados durante a correspondência de um URI candidato.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-223">The following code shows how default variable values are handled when matching a candidate URI.</span></span>  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/");

UriTemplate t = new UriTemplate("/{state=WA}/{city=Redmond}/", true);
Uri candidate = new Uri("http://localhost:8000/OR");

UriTemplateMatch m1 = t.Match(baseAddress, candidate);

Console.WriteLine($"Template: {t}");
Console.WriteLine($"Candidate URI: {candidate}");

// Display contents of BoundVariables
Console.WriteLine("BoundVariables:");
foreach (string key in m1.BoundVariables.AllKeys)
{
    Console.WriteLine($"\t{key}={m1.BoundVariables[key]}");
}
// The output of the above code is  
// Template: /{state=WA}/{city=Redmond}/
// Candidate URI: http://localhost:8000/OR
// BoundVariables:
//         STATE=OR
//         CITY=Redmond
```  
  
> [!NOTE]
> <span data-ttu-id="2ff7d-224">Um URI, como `http://localhost:8000///` não coincide com o modelo listado no código anterior, porém um URI, como `http://localhost:8000/` faz.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-224">A URI such as `http://localhost:8000///` does not match the template listed in the preceding code, however a URI such as `http://localhost:8000/` does.</span></span>  
  
 <span data-ttu-id="2ff7d-225">O código a seguir mostra como os valores de variáveis padrão são tratados durante a criação de um URI com um modelo.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-225">The following code shows how default variable values are handled when creating a URI with a template.</span></span>  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/");  
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);  
NameValueCollection vals = new NameValueCollection();  
vals.Add("a", "10");  
  
Uri boundUri = t.BindByName(baseAddress, vals);  
Console.WriteLine("BaseAddress: {0}", baseAddress);  
Console.WriteLine("Template: {0}", t.ToString());  
  
Console.WriteLine("Values: ");  
foreach (string key in vals.AllKeys)  
{  
    Console.WriteLine("\tKey = {0}, Value = {1}", key, vals[key]);  
}  
Console.WriteLine("Bound URI: {0}", boundUri);  
  
// The output of the preceding code is  
// BaseAddress: http://localhost:8000/  
// Template: /test/{a}/{b}  
// Values:  
//     Key = a, Value = 10  
// Bound URI: http://localhost:8000/test/10/5  
```  
  
<span data-ttu-id="2ff7d-226">Quando uma variável recebe um valor padrão de `null` há algumas restrições adicionais.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-226">When a variable is given a default value of `null` there are some additional constraints.</span></span> <span data-ttu-id="2ff7d-227">Uma variável pode ter um valor padrão de `null` se a variável está contida no segmento mais à direita da cadeia de caracteres de modelo ou se todos os segmentos à direita do segmento têm valores padrão de `null`.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-227">A variable can have a default value of `null` if the variable is contained within the right most segment of the template string or if all segments to the right of the segment have default values of `null`.</span></span> <span data-ttu-id="2ff7d-228">A seguir é cadeias de caracteres de modelo válido com valores padrão de `null`:</span><span class="sxs-lookup"><span data-stu-id="2ff7d-228">The following are valid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 <span data-ttu-id="2ff7d-229">A seguir é cadeias de caracteres de modelo inválido com valores padrão de `null`:</span><span class="sxs-lookup"><span data-stu-id="2ff7d-229">The following are invalid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a><span data-ttu-id="2ff7d-230">Correspondência e os valores padrão</span><span class="sxs-lookup"><span data-stu-id="2ff7d-230">Default Values and Matching</span></span>  
 <span data-ttu-id="2ff7d-231">Ao fazer a correspondência de um candidato URI com um modelo que tem valores padrão, os valores padrão são colocados no <xref:System.UriTemplateMatch.BoundVariables%2A> coleção se os valores não são especificados em que o URI candidato.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-231">When matching a candidate URI with a template that has default values, the default values are placed in the <xref:System.UriTemplateMatch.BoundVariables%2A> collection if values are not specified in the candidate URI.</span></span>  
  
### <a name="template-equivalence"></a><span data-ttu-id="2ff7d-232">Equivalência de modelo</span><span class="sxs-lookup"><span data-stu-id="2ff7d-232">Template Equivalence</span></span>  
 <span data-ttu-id="2ff7d-233">Dois modelos são considerados *estruturalmente equivalente* quando todos os literais dos modelos correspondem e têm variáveis nos mesmos segmentos.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-233">Two templates are said to be *structurally equivalent* when all of the templates' literals match and they have variables in the same segments.</span></span> <span data-ttu-id="2ff7d-234">Por exemplo, os seguintes modelos são estruturalmente equivalentes:</span><span class="sxs-lookup"><span data-stu-id="2ff7d-234">For example the following templates are structurally equivalent:</span></span>  
  
- <span data-ttu-id="2ff7d-235">/a/{var1}/b b/{var2}?x=1&y=2</span><span class="sxs-lookup"><span data-stu-id="2ff7d-235">/a/{var1}/b b/{var2}?x=1&y=2</span></span>  
  
- <span data-ttu-id="2ff7d-236">a/{x}/b%20b/{var1}?y=2&x=1</span><span class="sxs-lookup"><span data-stu-id="2ff7d-236">a/{x}/b%20b/{var1}?y=2&x=1</span></span>  
  
- <span data-ttu-id="2ff7d-237">a/{y}/B%20B/{z}/?y=2&x=1</span><span class="sxs-lookup"><span data-stu-id="2ff7d-237">a/{y}/B%20B/{z}/?y=2&x=1</span></span>  
  
 <span data-ttu-id="2ff7d-238">Algumas coisas a observar:</span><span class="sxs-lookup"><span data-stu-id="2ff7d-238">A few things to notice:</span></span>  
  
- <span data-ttu-id="2ff7d-239">Se um modelo contém barras à esquerda, somente o primeiro deles será ignorado.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-239">If a template contains leading slashes, only the first one is ignored.</span></span>  
  
- <span data-ttu-id="2ff7d-240">Ao comparar cadeias de caracteres de modelo para equivalência estrutural, caso é ignorado para nomes de variáveis e segmentos de caminho, cadeias de caracteres de consulta diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-240">When comparing template strings for structural equivalence, case is ignored for variable names and path segments, query strings are case sensitive.</span></span>  
  
- <span data-ttu-id="2ff7d-241">Cadeias de caracteres de consulta são ordenadas.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-241">Query strings are unordered.</span></span>  
  
## <a name="uritemplatetable"></a><span data-ttu-id="2ff7d-242">UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="2ff7d-242">UriTemplateTable</span></span>  
 <span data-ttu-id="2ff7d-243">O <xref:System.UriTemplateTable> classe representa uma tabela associativa de <xref:System.UriTemplate> objetos associados a um objeto do desenvolvedor do escolhendo.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-243">The <xref:System.UriTemplateTable> class represents an associative table of <xref:System.UriTemplate> objects bound to an object of the developer's choosing.</span></span> <span data-ttu-id="2ff7d-244">Um <xref:System.UriTemplateTable> deve conter pelo menos um <xref:System.UriTemplate> antes de chamar <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-244">A <xref:System.UriTemplateTable> must contain at least one <xref:System.UriTemplate> prior to calling <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span> <span data-ttu-id="2ff7d-245">O conteúdo de um <xref:System.UriTemplateTable> pode ser alterada até <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> é chamado.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-245">The contents of a <xref:System.UriTemplateTable> can be changed until <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="2ff7d-246">A validação é executada quando <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> é chamado.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-246">Validation is performed when <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="2ff7d-247">O tipo de validação executada depende do valor de `allowMultiple` parâmetro para <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-247">The type of validation performed depends upon the value of the `allowMultiple` parameter to <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span>  
  
 <span data-ttu-id="2ff7d-248">Quando <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> é chamado passando `false`, o <xref:System.UriTemplateTable> verificações para garantir que não existem modelos na tabela.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-248">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `false`, the <xref:System.UriTemplateTable> checks to make sure there are no templates in the table.</span></span> <span data-ttu-id="2ff7d-249">Se ele encontrar quaisquer modelos estruturalmente equivalentes, ele gerará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-249">If it finds any structurally equivalent templates, it throws an exception.</span></span> <span data-ttu-id="2ff7d-250">Isso é usado em conjunto com <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> quando você deseja garantir que apenas um modelo corresponde a um URI de entrada.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-250">This is used in conjunction with <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> when you want to ensure only one template matches an incoming URI.</span></span>  
  
 <span data-ttu-id="2ff7d-251">Quando <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> é chamado passando `true`, <xref:System.UriTemplateTable> permite que vários modelos estruturalmente equivalente a ser contido dentro de um <xref:System.UriTemplateTable>.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-251">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `true`, <xref:System.UriTemplateTable> allows multiple, structurally-equivalent templates to be contained within a <xref:System.UriTemplateTable>.</span></span>  
  
 <span data-ttu-id="2ff7d-252">Se um conjunto de <xref:System.UriTemplate> objetos adicionados a um <xref:System.UriTemplateTable> contêm cadeias de caracteres de consulta não deve ser ambíguas.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-252">If a set of <xref:System.UriTemplate> objects added to a <xref:System.UriTemplateTable> contain query strings they must not be ambiguous.</span></span> <span data-ttu-id="2ff7d-253">Cadeias de caracteres de consulta idênticos são permitidas.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-253">Identical query strings are allowed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ff7d-254">Enquanto o <xref:System.UriTemplateTable> permite que a base de dados de endereços que esquemas de uso diferente de HTTP, o esquema e número da porta são ignorados durante a correspondência de URIs candidatos aos modelos.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-254">While the <xref:System.UriTemplateTable> allows base addresses that use schemes other than HTTP, the scheme and port number are ignored when matching candidate URIs to templates.</span></span>  
  
### <a name="query-string-ambiguity"></a><span data-ttu-id="2ff7d-255">Ambiguidade da cadeia de caracteres de consulta</span><span class="sxs-lookup"><span data-stu-id="2ff7d-255">Query String Ambiguity</span></span>  
 <span data-ttu-id="2ff7d-256">Modelos que compartilham um caminho equivalente contêm cadeias de caracteres de consulta ambígua se não houver um URI que corresponde a mais de um modelo.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-256">Templates that share an equivalent path contain ambiguous query strings if there is a URI that matches more than one template.</span></span>  
  
 <span data-ttu-id="2ff7d-257">Os seguintes conjuntos de cadeias de caracteres de consulta são não ambíguos em si mesmos:</span><span class="sxs-lookup"><span data-stu-id="2ff7d-257">The following sets of query strings are unambiguous within themselves:</span></span>  
  
- <span data-ttu-id="2ff7d-258">?x=1</span><span class="sxs-lookup"><span data-stu-id="2ff7d-258">?x=1</span></span>  
  
- <span data-ttu-id="2ff7d-259">?x=2</span><span class="sxs-lookup"><span data-stu-id="2ff7d-259">?x=2</span></span>  
  
- <span data-ttu-id="2ff7d-260">?x=3</span><span class="sxs-lookup"><span data-stu-id="2ff7d-260">?x=3</span></span>  
  
- <span data-ttu-id="2ff7d-261">?x=1&y={var}</span><span class="sxs-lookup"><span data-stu-id="2ff7d-261">?x=1&y={var}</span></span>  
  
- <span data-ttu-id="2ff7d-262">?x=2&z={var}</span><span class="sxs-lookup"><span data-stu-id="2ff7d-262">?x=2&z={var}</span></span>  
  
- <span data-ttu-id="2ff7d-263">?x=3</span><span class="sxs-lookup"><span data-stu-id="2ff7d-263">?x=3</span></span>  
  
- <span data-ttu-id="2ff7d-264">?x=1</span><span class="sxs-lookup"><span data-stu-id="2ff7d-264">?x=1</span></span>  
  
- <span data-ttu-id="2ff7d-265">?</span><span class="sxs-lookup"><span data-stu-id="2ff7d-265">?</span></span>  
  
- <span data-ttu-id="2ff7d-266">?</span><span class="sxs-lookup"><span data-stu-id="2ff7d-266">?</span></span> <span data-ttu-id="2ff7d-267">x={var}</span><span class="sxs-lookup"><span data-stu-id="2ff7d-267">x={var}</span></span>  
  
- <span data-ttu-id="2ff7d-268">?</span><span class="sxs-lookup"><span data-stu-id="2ff7d-268">?</span></span>  
  
- <span data-ttu-id="2ff7d-269">?m=get&c=rss</span><span class="sxs-lookup"><span data-stu-id="2ff7d-269">?m=get&c=rss</span></span>  
  
- <span data-ttu-id="2ff7d-270">?m=put&c=rss</span><span class="sxs-lookup"><span data-stu-id="2ff7d-270">?m=put&c=rss</span></span>  
  
- <span data-ttu-id="2ff7d-271">?m=get&c=atom</span><span class="sxs-lookup"><span data-stu-id="2ff7d-271">?m=get&c=atom</span></span>  
  
- <span data-ttu-id="2ff7d-272">?m=put&c=atom</span><span class="sxs-lookup"><span data-stu-id="2ff7d-272">?m=put&c=atom</span></span>  
  
 <span data-ttu-id="2ff7d-273">Os seguintes conjuntos de modelos de cadeia de caracteres de consulta são ambíguos em si mesmos:</span><span class="sxs-lookup"><span data-stu-id="2ff7d-273">The following sets of query string templates are ambiguous within themselves:</span></span>  
  
- <span data-ttu-id="2ff7d-274">?x=1</span><span class="sxs-lookup"><span data-stu-id="2ff7d-274">?x=1</span></span>  
  
- <span data-ttu-id="2ff7d-275">?x={var}</span><span class="sxs-lookup"><span data-stu-id="2ff7d-275">?x={var}</span></span>  
  
 <span data-ttu-id="2ff7d-276">"x = 1"-corresponde a ambos os modelos.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-276">"x=1" - Matches both templates.</span></span>  
  
- <span data-ttu-id="2ff7d-277">?x=1</span><span class="sxs-lookup"><span data-stu-id="2ff7d-277">?x=1</span></span>  
  
- <span data-ttu-id="2ff7d-278">?y=2</span><span class="sxs-lookup"><span data-stu-id="2ff7d-278">?y=2</span></span>  
  
 <span data-ttu-id="2ff7d-279">"x = 1 & y = 2" corresponde a ambos os modelos.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-279">"x=1&y=2" matches both templates.</span></span> <span data-ttu-id="2ff7d-280">Isso ocorre porque uma cadeia de caracteres de consulta pode conter mais variáveis de cadeia de caracteres de consulta e em seguida, o modelo que ela corresponde.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-280">This is because a query string may contain more query string variables then the template it matches.</span></span>  
  
- <span data-ttu-id="2ff7d-281">?x=1</span><span class="sxs-lookup"><span data-stu-id="2ff7d-281">?x=1</span></span>  
  
- <span data-ttu-id="2ff7d-282">?x=1&y={var}</span><span class="sxs-lookup"><span data-stu-id="2ff7d-282">?x=1&y={var}</span></span>  
  
 <span data-ttu-id="2ff7d-283">"x = 1 & y = 3" corresponde a ambos os modelos.</span><span class="sxs-lookup"><span data-stu-id="2ff7d-283">"x=1&y=3" matches both templates.</span></span>  
  
- <span data-ttu-id="2ff7d-284">?x=3&y=4</span><span class="sxs-lookup"><span data-stu-id="2ff7d-284">?x=3&y=4</span></span>  
  
- <span data-ttu-id="2ff7d-285">?x=3&z=5</span><span class="sxs-lookup"><span data-stu-id="2ff7d-285">?x=3&z=5</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ff7d-286">Os caracteres á e Á são considerados diferentes caracteres quando eles são exibidos como parte de um caminho de URI ou <xref:System.UriTemplate> literal do segmento de caminho (mas os caracteres a e A são considerados para ser o mesmo).</span><span class="sxs-lookup"><span data-stu-id="2ff7d-286">The characters á and Á are considered to be different characters when they appear as part of a URI path or <xref:System.UriTemplate> path segment literal (but the characters a and A are considered to be the same).</span></span> <span data-ttu-id="2ff7d-287">Os caracteres á e Á são considerados os mesmos caracteres quando eles são exibidos como parte de um <xref:System.UriTemplate> {variableName} ou uma cadeia de caracteres de consulta (e a e também são considerados para ser os mesmos caracteres).</span><span class="sxs-lookup"><span data-stu-id="2ff7d-287">The characters á and Á are considered to be the same characters when they appear as part of a <xref:System.UriTemplate> {variableName} or a query string (and a and A are also considered to be the same characters).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff7d-288">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ff7d-288">See also</span></span>

- [<span data-ttu-id="2ff7d-289">Visão geral do modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="2ff7d-289">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="2ff7d-290">Modelo de objeto de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="2ff7d-290">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [<span data-ttu-id="2ff7d-291">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="2ff7d-291">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
- [<span data-ttu-id="2ff7d-292">Tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="2ff7d-292">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="2ff7d-293">Dispatcher de Tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="2ff7d-293">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
