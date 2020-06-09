---
title: UriTemplate and UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: 106ba21b58dabab96afbc8fb6db5cb305386f2fe
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595070"
---
# <a name="uritemplate-and-uritemplatetable"></a><span data-ttu-id="d0803-102">UriTemplate and UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="d0803-102">UriTemplate and UriTemplateTable</span></span>
<span data-ttu-id="d0803-103">Os desenvolvedores da Web exigem a capacidade de descrever a forma e o layout dos URIs aos quais seus serviços respondem.</span><span class="sxs-lookup"><span data-stu-id="d0803-103">Web developers require the ability to describe the shape and layout of the URIs that their services respond to.</span></span> <span data-ttu-id="d0803-104">Windows Communication Foundation (WCF) adicionou duas novas classes para dar aos desenvolvedores controle sobre seus URIs.</span><span class="sxs-lookup"><span data-stu-id="d0803-104">Windows Communication Foundation (WCF) added two new classes to give developers control over their URIs.</span></span> <span data-ttu-id="d0803-105"><xref:System.UriTemplate>e <xref:System.UriTemplateTable> forma a base do mecanismo de expedição baseado em URI no WCF.</span><span class="sxs-lookup"><span data-stu-id="d0803-105"><xref:System.UriTemplate> and <xref:System.UriTemplateTable> form the basis of the URI-based dispatch engine in WCF.</span></span> <span data-ttu-id="d0803-106">Essas classes também podem ser usadas por conta própria, permitindo que os desenvolvedores tirem proveito dos modelos e do mecanismo de mapeamento de URI sem implementar um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="d0803-106">These classes can also be used on their own, allowing developers to take advantage of templates and the URI mapping mechanism without implementing a WCF service.</span></span>  
  
## <a name="templates"></a><span data-ttu-id="d0803-107">Modelos</span><span class="sxs-lookup"><span data-stu-id="d0803-107">Templates</span></span>  
 <span data-ttu-id="d0803-108">Um modelo é uma maneira de descrever um conjunto de URIs relativos.</span><span class="sxs-lookup"><span data-stu-id="d0803-108">A template is a way to describe a set of relative URIs.</span></span> <span data-ttu-id="d0803-109">O conjunto de modelos de URI na tabela a seguir mostra como um sistema que recupera vários tipos de informações de clima pode ser definido.</span><span class="sxs-lookup"><span data-stu-id="d0803-109">The set of URI templates in the following table shows how a system that retrieves various types of weather information might be defined.</span></span>  
  
|<span data-ttu-id="d0803-110">Dados</span><span class="sxs-lookup"><span data-stu-id="d0803-110">Data</span></span>|<span data-ttu-id="d0803-111">Modelo</span><span class="sxs-lookup"><span data-stu-id="d0803-111">Template</span></span>|  
|----------|--------------|  
|<span data-ttu-id="d0803-112">Previsão nacional</span><span class="sxs-lookup"><span data-stu-id="d0803-112">National Forecast</span></span>|<span data-ttu-id="d0803-113">clima/nacional</span><span class="sxs-lookup"><span data-stu-id="d0803-113">weather/national</span></span>|  
|<span data-ttu-id="d0803-114">Previsão de estado</span><span class="sxs-lookup"><span data-stu-id="d0803-114">State Forecast</span></span>|<span data-ttu-id="d0803-115">clima/{estado}</span><span class="sxs-lookup"><span data-stu-id="d0803-115">weather/{state}</span></span>|  
|<span data-ttu-id="d0803-116">Previsão de cidade</span><span class="sxs-lookup"><span data-stu-id="d0803-116">City Forecast</span></span>|<span data-ttu-id="d0803-117">clima/{estado}/{cidade}</span><span class="sxs-lookup"><span data-stu-id="d0803-117">weather/{state}/{city}</span></span>|  
|<span data-ttu-id="d0803-118">Previsão de atividade</span><span class="sxs-lookup"><span data-stu-id="d0803-118">Activity Forecast</span></span>|<span data-ttu-id="d0803-119">clima/{estado}/{cidade}/{atividade}</span><span class="sxs-lookup"><span data-stu-id="d0803-119">weather/{state}/{city}/{activity}</span></span>|  
  
 <span data-ttu-id="d0803-120">Esta tabela descreve um conjunto de URIs estruturalmente semelhantes.</span><span class="sxs-lookup"><span data-stu-id="d0803-120">This table describes a set of structurally similar URIs.</span></span> <span data-ttu-id="d0803-121">Cada entrada é um modelo de URI.</span><span class="sxs-lookup"><span data-stu-id="d0803-121">Each entry is a URI template.</span></span> <span data-ttu-id="d0803-122">Os segmentos entre chaves descrevem as variáveis.</span><span class="sxs-lookup"><span data-stu-id="d0803-122">The segments in curly braces describe variables.</span></span> <span data-ttu-id="d0803-123">Os segmentos que não estão entre chaves descrevem cadeias de caracteres literais.</span><span class="sxs-lookup"><span data-stu-id="d0803-123">The segments not in curly braces describe literal strings.</span></span> <span data-ttu-id="d0803-124">As classes de modelo do WCF permitem que um desenvolvedor Use um URI de entrada, por exemplo, "/Weather/wa/Seattle/Cycling" e faça a correspondência com um modelo que o descreva, "/Weather/{State}/{City}/{Activity}".</span><span class="sxs-lookup"><span data-stu-id="d0803-124">The WCF template classes allow a developer to take an incoming URI, for example, "/weather/wa/seattle/cycling", and match it to a template that describes it, "/weather/{state}/{city}/{activity}".</span></span>  
  
## <a name="uritemplate"></a><span data-ttu-id="d0803-125">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="d0803-125">UriTemplate</span></span>  
 <span data-ttu-id="d0803-126"><xref:System.UriTemplate>é uma classe que encapsula um modelo de URI.</span><span class="sxs-lookup"><span data-stu-id="d0803-126"><xref:System.UriTemplate> is a class that encapsulates a URI template.</span></span> <span data-ttu-id="d0803-127">O construtor usa um parâmetro de cadeia de caracteres que define o modelo.</span><span class="sxs-lookup"><span data-stu-id="d0803-127">The constructor takes a string parameter that defines the template.</span></span> <span data-ttu-id="d0803-128">Essa cadeia de caracteres contém o modelo no formato descrito na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="d0803-128">This string contains the template in the format described in the next section.</span></span> <span data-ttu-id="d0803-129">A <xref:System.UriTemplate> classe fornece métodos que permitem que você corresponda a um URI de entrada para um modelo, gere um URI a partir de um modelo, recupere uma coleção de nomes de variáveis usados no modelo, determine se dois modelos são equivalentes e retorna a cadeia de caracteres do modelo.</span><span class="sxs-lookup"><span data-stu-id="d0803-129">The <xref:System.UriTemplate> class provides methods that allow you match an incoming URI to a template, generate a URI from a template, retrieve a collection of variable names used in the template, determine whether two templates are equivalent, and return the template's string.</span></span>  
  
 <span data-ttu-id="d0803-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29>usa um endereço base e um URI candidato e tenta corresponder o URI ao modelo.</span><span class="sxs-lookup"><span data-stu-id="d0803-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> takes a base address and a candidate URI and attempts to match the URI to the template.</span></span> <span data-ttu-id="d0803-131">Se a correspondência for bem-sucedida, uma <xref:System.UriTemplateMatch> instância será retornada.</span><span class="sxs-lookup"><span data-stu-id="d0803-131">If the match is successful, a <xref:System.UriTemplateMatch> instance is returned.</span></span> <span data-ttu-id="d0803-132">O <xref:System.UriTemplateMatch> objeto contém um URI de base, o URI candidato, uma coleção de nome/valor dos parâmetros de consulta, uma matriz dos segmentos de caminho relativo, uma coleção de nome/valor de variáveis que foram correspondidas, a <xref:System.UriTemplate> instância usada para executar a correspondência, uma cadeia de caracteres que contém qualquer parte não correspondente do URI candidato (usada quando o modelo tem um curinga) e um objeto associado ao modelo.</span><span class="sxs-lookup"><span data-stu-id="d0803-132">The <xref:System.UriTemplateMatch> object contains a base URI, the candidate URI, a name/value collection of the query parameters, an array of the relative path segments, a name/value collection of variables that were matched, the <xref:System.UriTemplate> instance used to perform the match, a string that contains any unmatched portion of the candidate URI (used when the template has a wildcard), and an object that is associated with the template.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0803-133">A <xref:System.UriTemplate> classe ignora o esquema e o número da porta ao corresponder um URI candidato a um modelo.</span><span class="sxs-lookup"><span data-stu-id="d0803-133">The <xref:System.UriTemplate> class ignores the scheme and port number when matching a candidate URI to a template.</span></span>  
  
 <span data-ttu-id="d0803-134">Há dois métodos que permitem gerar um URI a partir de um modelo <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> e <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> .</span><span class="sxs-lookup"><span data-stu-id="d0803-134">There are two methods that allow you to generate a URI from a template, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> and <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span></span> <span data-ttu-id="d0803-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29>usa um endereço base e uma coleção de nome/valor de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d0803-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> takes a base address and a name/value collection of parameters.</span></span> <span data-ttu-id="d0803-136">Esses parâmetros são substituídos por variáveis quando o modelo é associado.</span><span class="sxs-lookup"><span data-stu-id="d0803-136">These parameters are substituted for variables when the template is bound.</span></span> <span data-ttu-id="d0803-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>usa os pares de nome/valor e os substitui da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="d0803-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> takes the name/value pairs and substitutes them left to right.</span></span>  
  
 <span data-ttu-id="d0803-138"><xref:System.UriTemplate.ToString>Retorna a cadeia de caracteres do modelo.</span><span class="sxs-lookup"><span data-stu-id="d0803-138"><xref:System.UriTemplate.ToString> returns the template string.</span></span>  
  
 <span data-ttu-id="d0803-139">A <xref:System.UriTemplate.PathSegmentVariableNames%2A> propriedade contém uma coleção dos nomes das variáveis usadas em segmentos de caminho na cadeia de caracteres do modelo.</span><span class="sxs-lookup"><span data-stu-id="d0803-139">The <xref:System.UriTemplate.PathSegmentVariableNames%2A> property contains a collection of the names of the variables used within path segments in the template string.</span></span>  
  
 <span data-ttu-id="d0803-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29>usa um <xref:System.UriTemplate> como parâmetro e retorna um valor booliano que especifica se os dois modelos são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="d0803-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> takes a <xref:System.UriTemplate> as a parameter and returns a Boolean value that specifies whether the two templates are equivalent.</span></span> <span data-ttu-id="d0803-141">Para obter mais informações, consulte a seção equivalência de modelo mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="d0803-141">For more information, see the Template Equivalence section later in this topic.</span></span>  
  
 <span data-ttu-id="d0803-142"><xref:System.UriTemplate>foi projetado para funcionar com qualquer esquema URI que esteja de acordo com a gramática de HTTP URI.</span><span class="sxs-lookup"><span data-stu-id="d0803-142"><xref:System.UriTemplate> is designed to work with any URI scheme that conforms to the HTTP URI grammar.</span></span> <span data-ttu-id="d0803-143">Veja a seguir exemplos de esquemas de URI com suporte.</span><span class="sxs-lookup"><span data-stu-id="d0803-143">The following are examples of supported URI schemes.</span></span>  
  
- `http://`  
  
- `https://`  
  
- `net.tcp://`  
  
- `net.pipe://`  
  
- `sb://`  
  
 <span data-ttu-id="d0803-144">Esquemas como file://e urn://não estão em conformidade com a gramática de HTTP URI e causam resultados imprevisíveis quando usados com modelos de URI.</span><span class="sxs-lookup"><span data-stu-id="d0803-144">Schemes like file:// and urn:// do not conform to the HTTP URI grammar and cause unpredictable results when used with URI templates.</span></span>  
  
### <a name="template-string-syntax"></a><span data-ttu-id="d0803-145">Sintaxe de cadeia de caracteres de modelo</span><span class="sxs-lookup"><span data-stu-id="d0803-145">Template String Syntax</span></span>  
 <span data-ttu-id="d0803-146">Um modelo tem três partes: um caminho, uma consulta opcional e um fragmento opcional.</span><span class="sxs-lookup"><span data-stu-id="d0803-146">A template has three parts: a path, an optional query, and an optional fragment.</span></span> <span data-ttu-id="d0803-147">Para obter um exemplo, consulte o seguinte modelo:</span><span class="sxs-lookup"><span data-stu-id="d0803-147">For an example, see the following template:</span></span>  
  
`"/weather/{state}/{city}?forecast={length)#frag1`  
  
 <span data-ttu-id="d0803-148">O caminho consiste em "/Weather/{State}/{City}", a consulta consiste em "? previsão = {Length} e o fragmento consiste em" #frag1 ".</span><span class="sxs-lookup"><span data-stu-id="d0803-148">The path consists of "/weather/{state}/{city}", the query consists of "?forecast={length}, and the fragment consists of "#frag1".</span></span>  
  
 <span data-ttu-id="d0803-149">As barras à esquerda e à direita são opcionais na expressão de caminho.</span><span class="sxs-lookup"><span data-stu-id="d0803-149">Leading and trailing slashes are optional in the path expression.</span></span> <span data-ttu-id="d0803-150">Tanto as expressões de consulta quanto de fragmento podem ser omitidas inteiramente.</span><span class="sxs-lookup"><span data-stu-id="d0803-150">Both the query and fragment expressions can be omitted entirely.</span></span> <span data-ttu-id="d0803-151">Um caminho consiste em uma série de segmentos delimitados por '/', cada segmento pode ter um valor literal, um nome de variável (escrito em {keycolchetes}) ou um curinga (gravado como ' \* ').</span><span class="sxs-lookup"><span data-stu-id="d0803-151">A path consists of a series of segments delimited by '/', each segment can have a literal value, a variable name (written in {curly braces}), or a wildcard (written as '\*').</span></span> <span data-ttu-id="d0803-152">No modelo anterior, o "segmento \weather\ é um valor literal enquanto" {State} "e" {City} "são variáveis.</span><span class="sxs-lookup"><span data-stu-id="d0803-152">In the previous template the "\weather\ segment is a literal value while "{state}" and "{city}" are variables.</span></span> <span data-ttu-id="d0803-153">As variáveis recebem seu nome do conteúdo de suas chaves e elas podem ser substituídas posteriormente por um valor concreto para criar um *URI fechado*.</span><span class="sxs-lookup"><span data-stu-id="d0803-153">Variables take their name from the contents of their curly braces and they can later be replaced with a concrete value to create a *closed URI*.</span></span> <span data-ttu-id="d0803-154">O curinga é opcional, mas só pode aparecer no final do URI, onde ele corresponde logicamente a "o restante do caminho".</span><span class="sxs-lookup"><span data-stu-id="d0803-154">The wildcard is optional, but can only appear at the end of the URI, where it logically matches "the rest of the path".</span></span>  
  
 <span data-ttu-id="d0803-155">A expressão de consulta, se presente, especifica uma série de pares de nome/valor não ordenados delimitadas por ' & '.</span><span class="sxs-lookup"><span data-stu-id="d0803-155">The query expression, if present, specifies a series of unordered name/value pairs delimited by '&'.</span></span> <span data-ttu-id="d0803-156">Os elementos da expressão de consulta podem ser pares literais (x = 2) ou um par de variáveis (x = {var}).</span><span class="sxs-lookup"><span data-stu-id="d0803-156">Elements of the query expression can either be literal pairs (x=2) or a variable pair (x={var}).</span></span> <span data-ttu-id="d0803-157">Somente o lado direito da consulta pode ter uma expressão variável.</span><span class="sxs-lookup"><span data-stu-id="d0803-157">Only the right side of the query can have a variable expression.</span></span> <span data-ttu-id="d0803-158">({somename} = {someValue} não é permitido.</span><span class="sxs-lookup"><span data-stu-id="d0803-158">({someName} = {someValue} is not allowed.</span></span> <span data-ttu-id="d0803-159">Valores não emparelhados (? x) não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="d0803-159">Unpaired values (?x) are not permitted.</span></span> <span data-ttu-id="d0803-160">Não há nenhuma diferença entre uma expressão de consulta vazia e uma expressão de consulta consistindo apenas em um único '? ' (ambos significam "qualquer consulta").</span><span class="sxs-lookup"><span data-stu-id="d0803-160">There is no difference between an empty query expression and a query expression consisting of just a single '?' (both mean "any query").</span></span>  
  
 <span data-ttu-id="d0803-161">A expressão de fragmento pode consistir em um valor literal, nenhuma variável é permitida.</span><span class="sxs-lookup"><span data-stu-id="d0803-161">The fragment expression can consist of a literal value, no variables are allowed.</span></span>  
  
 <span data-ttu-id="d0803-162">Todos os nomes de variáveis de modelo dentro de uma cadeia de caracteres de modelo devem ser exclusivos.</span><span class="sxs-lookup"><span data-stu-id="d0803-162">All template variable names within a template string must be unique.</span></span> <span data-ttu-id="d0803-163">Os nomes de variáveis de modelo não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="d0803-163">Template variable names are case-insensitive.</span></span>  
  
 <span data-ttu-id="d0803-164">Exemplos de cadeias de caracteres de modelo válidas:</span><span class="sxs-lookup"><span data-stu-id="d0803-164">Examples of valid template strings:</span></span>  
  
- <span data-ttu-id="d0803-165">""</span><span class="sxs-lookup"><span data-stu-id="d0803-165">""</span></span>  
  
- <span data-ttu-id="d0803-166">"/shoe"</span><span class="sxs-lookup"><span data-stu-id="d0803-166">"/shoe"</span></span>  
  
- <span data-ttu-id="d0803-167">"/Shoe/ \* "</span><span class="sxs-lookup"><span data-stu-id="d0803-167">"/shoe/\*"</span></span>  
  
- <span data-ttu-id="d0803-168">"{sapato}/Boat"</span><span class="sxs-lookup"><span data-stu-id="d0803-168">"{shoe}/boat"</span></span>  
  
- <span data-ttu-id="d0803-169">"{sapato}/{Boat}/Bed/{Quilt}"</span><span class="sxs-lookup"><span data-stu-id="d0803-169">"{shoe}/{boat}/bed/{quilt}"</span></span>  
  
- <span data-ttu-id="d0803-170">"sapato/{barco}"</span><span class="sxs-lookup"><span data-stu-id="d0803-170">"shoe/{boat}"</span></span>  
  
- <span data-ttu-id="d0803-171">"sapato/{barco}/ \* "</span><span class="sxs-lookup"><span data-stu-id="d0803-171">"shoe/{boat}/\*"</span></span>  
  
- <span data-ttu-id="d0803-172">"sapato/barco? x = 2"</span><span class="sxs-lookup"><span data-stu-id="d0803-172">"shoe/boat?x=2"</span></span>  
  
- <span data-ttu-id="d0803-173">"sapato/{barco}? x = {cama}"</span><span class="sxs-lookup"><span data-stu-id="d0803-173">"shoe/{boat}?x={bed}"</span></span>  
  
- <span data-ttu-id="d0803-174">"sapato/{barco}? x = {cama} &y = banda"</span><span class="sxs-lookup"><span data-stu-id="d0803-174">"shoe/{boat}?x={bed}&y=band"</span></span>  
  
- <span data-ttu-id="d0803-175">"? x = {sapato}"</span><span class="sxs-lookup"><span data-stu-id="d0803-175">"?x={shoe}"</span></span>  
  
- <span data-ttu-id="d0803-176">"sapato? x = 3&y = {var}</span><span class="sxs-lookup"><span data-stu-id="d0803-176">"shoe?x=3&y={var}</span></span>  
  
 <span data-ttu-id="d0803-177">Exemplos de cadeias de caracteres de modelo inválidas:</span><span class="sxs-lookup"><span data-stu-id="d0803-177">Examples of invalid template strings:</span></span>  
  
- <span data-ttu-id="d0803-178">"{sapato}/{SHOE}/x = 2" – nomes de variáveis duplicados.</span><span class="sxs-lookup"><span data-stu-id="d0803-178">"{shoe}/{SHOE}/x=2" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="d0803-179">"{sapato}/Boat/? cama = {sapato}" – nomes de variáveis duplicados.</span><span class="sxs-lookup"><span data-stu-id="d0803-179">"{shoe}/boat/?bed={shoe}" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="d0803-180">"? x = 2&x = 3" – os pares de nome/valor dentro de uma cadeia de caracteres de consulta devem ser exclusivos, mesmo que sejam literais.</span><span class="sxs-lookup"><span data-stu-id="d0803-180">"?x=2&x=3" – Name/value pairs within a query string must be unique, even if they are literals.</span></span>  
  
- <span data-ttu-id="d0803-181">"? x = 2&" – a cadeia de caracteres de consulta está malformada.</span><span class="sxs-lookup"><span data-stu-id="d0803-181">"?x=2&" – Query string is malformed.</span></span>  
  
- <span data-ttu-id="d0803-182">"? 2&x = {sapato}" – a cadeia de caracteres de consulta deve ser pares de nome/valor.</span><span class="sxs-lookup"><span data-stu-id="d0803-182">"?2&x={shoe}" – Query string must be name/value pairs.</span></span>  
  
- <span data-ttu-id="d0803-183">"? y = 2&&X = 3" – a cadeia de caracteres de consulta deve ser pares de valor de nome, os nomes não podem começar com ' & '.</span><span class="sxs-lookup"><span data-stu-id="d0803-183">"?y=2&&X=3" – Query string must be name value pairs, names cannot start with '&'.</span></span>  
  
### <a name="compound-path-segments"></a><span data-ttu-id="d0803-184">Segmentos de caminho composto</span><span class="sxs-lookup"><span data-stu-id="d0803-184">Compound Path Segments</span></span>  
 <span data-ttu-id="d0803-185">Segmentos de caminho composto permitem que um único segmento de caminho de URI contenha várias variáveis, bem como variáveis combinadas com literais.</span><span class="sxs-lookup"><span data-stu-id="d0803-185">Compound path segments allow a single URI path segment to contain multiple variables as well as variables combined with literals.</span></span> <span data-ttu-id="d0803-186">Veja a seguir exemplos de segmentos de caminho composto válidos.</span><span class="sxs-lookup"><span data-stu-id="d0803-186">The following are examples of valid compound path segments.</span></span>  
  
- <span data-ttu-id="d0803-187">/filename. {ext}/</span><span class="sxs-lookup"><span data-stu-id="d0803-187">/filename.{ext}/</span></span>  
  
- <span data-ttu-id="d0803-188">/{filename}.jpg/</span><span class="sxs-lookup"><span data-stu-id="d0803-188">/{filename}.jpg/</span></span>  
  
- <span data-ttu-id="d0803-189">/{filename}. {ext}/</span><span class="sxs-lookup"><span data-stu-id="d0803-189">/{filename}.{ext}/</span></span>  
  
- <span data-ttu-id="d0803-190">um. {b} someLiteral {c} ({d})/</span><span class="sxs-lookup"><span data-stu-id="d0803-190">/{a}.{b}someLiteral{c}({d})/</span></span>  
  
 <span data-ttu-id="d0803-191">Veja a seguir exemplos de segmentos de caminho inválidos.</span><span class="sxs-lookup"><span data-stu-id="d0803-191">The following are examples of invalid path segments.</span></span>  
  
- <span data-ttu-id="d0803-192">As {} variáveis/devem ser nomeadas.</span><span class="sxs-lookup"><span data-stu-id="d0803-192">/{} - Variables must be named.</span></span>  
  
- <span data-ttu-id="d0803-193">/{Shoe}{Boat}-as variáveis devem ser separadas por um literal.</span><span class="sxs-lookup"><span data-stu-id="d0803-193">/{shoe}{boat} - Variables must be separated by a literal.</span></span>  
  
### <a name="matching-and-compound-path-segments"></a><span data-ttu-id="d0803-194">Correspondência e segmentos de caminho compostos</span><span class="sxs-lookup"><span data-stu-id="d0803-194">Matching and Compound Path Segments</span></span>  
 <span data-ttu-id="d0803-195">Segmentos de caminho composto permitem que você defina um UriTemplate que tenha várias variáveis dentro de um único segmento de caminho.</span><span class="sxs-lookup"><span data-stu-id="d0803-195">Compound path segments allow you to define a UriTemplate that has multiple variables within a single path segment.</span></span> <span data-ttu-id="d0803-196">Por exemplo, na seguinte cadeia de caracteres de modelo: "Addresses/{State}. {City} "duas variáveis (State e City) são definidas dentro do mesmo segmento.</span><span class="sxs-lookup"><span data-stu-id="d0803-196">For example, in the following template string: "Addresses/{state}.{city}" two variables (state and city) are defined within the same segment.</span></span> <span data-ttu-id="d0803-197">Esse modelo corresponderia a uma URL como `http://example.com/Washington.Redmond` , mas também corresponderá a uma URL como `http://example.com/Washington.Redmond.Microsoft` .</span><span class="sxs-lookup"><span data-stu-id="d0803-197">This template would match a URL such as `http://example.com/Washington.Redmond` but it will also match an URL like `http://example.com/Washington.Redmond.Microsoft`.</span></span> <span data-ttu-id="d0803-198">No último caso, a variável de estado conterá "Washington" e a variável City conterá "Redmond. Microsoft".</span><span class="sxs-lookup"><span data-stu-id="d0803-198">In the latter case, the state variable will contain "Washington" and the city variable will contain "Redmond.Microsoft".</span></span> <span data-ttu-id="d0803-199">Nesse caso, qualquer texto (exceto '/') corresponderá à variável {City}.</span><span class="sxs-lookup"><span data-stu-id="d0803-199">In this case any text (except ‘/’) will match the {city} variable.</span></span> <span data-ttu-id="d0803-200">Se você quiser um modelo que não corresponda ao texto "extra", coloque a variável em um segmento de modelo separado, por exemplo: "Addresses/{State}/{City}.</span><span class="sxs-lookup"><span data-stu-id="d0803-200">If you want a template that will not match the "extra" text, place the variable in a separate template segment, for example: "Addresses/{state}/{city}.</span></span>  
  
### <a name="named-wildcard-segments"></a><span data-ttu-id="d0803-201">Segmentos curinga nomeados</span><span class="sxs-lookup"><span data-stu-id="d0803-201">Named Wildcard Segments</span></span>  
 <span data-ttu-id="d0803-202">Um segmento curinga nomeado é qualquer segmento de variável de caminho cujo nome da variável comece com o caractere curinga ' \* '.</span><span class="sxs-lookup"><span data-stu-id="d0803-202">A named wildcard segment is any path variable segment whose variable name begins with the wildcard character ‘\*’.</span></span> <span data-ttu-id="d0803-203">A cadeia de caracteres de modelo a seguir contém um segmento curinga nomeado chamado "sapato".</span><span class="sxs-lookup"><span data-stu-id="d0803-203">The following template string contains a named wildcard segment named "shoe".</span></span>  
  
`"literal/{*shoe}"`  
  
 <span data-ttu-id="d0803-204">Os segmentos curinga devem seguir as seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="d0803-204">Wildcard segments must follow the following rules:</span></span>  
  
- <span data-ttu-id="d0803-205">Pode haver no máximo um segmento curinga nomeado para cada cadeia de caracteres de modelo.</span><span class="sxs-lookup"><span data-stu-id="d0803-205">There can be at most one named wildcard segment for each template string.</span></span>  
  
- <span data-ttu-id="d0803-206">Um segmento curinga nomeado deve aparecer no segmento mais à direita no caminho.</span><span class="sxs-lookup"><span data-stu-id="d0803-206">A named wildcard segment must appear at the right-most segment in the path.</span></span>  
  
- <span data-ttu-id="d0803-207">Um segmento curinga nomeado não pode coexistir com um segmento curinga anônimo dentro da mesma cadeia de caracteres de modelo.</span><span class="sxs-lookup"><span data-stu-id="d0803-207">A named wildcard segment cannot coexist with an anonymous wildcard segment within the same template string.</span></span>  
  
- <span data-ttu-id="d0803-208">O nome de um segmento curinga nomeado deve ser exclusivo.</span><span class="sxs-lookup"><span data-stu-id="d0803-208">The name of a named wildcard segment must be unique.</span></span>  
  
- <span data-ttu-id="d0803-209">Segmentos curinga nomeados não podem ter valores padrão.</span><span class="sxs-lookup"><span data-stu-id="d0803-209">Named wildcard segments cannot have default values.</span></span>  
  
- <span data-ttu-id="d0803-210">Segmentos curinga nomeados não podem terminar com "/".</span><span class="sxs-lookup"><span data-stu-id="d0803-210">Named wildcard segments cannot end with "/".</span></span>  
  
### <a name="default-variable-values"></a><span data-ttu-id="d0803-211">Valores de variáveis padrão</span><span class="sxs-lookup"><span data-stu-id="d0803-211">Default Variable Values</span></span>  
 <span data-ttu-id="d0803-212">Valores de variáveis padrão permitem que você especifique valores padrão para variáveis dentro de um modelo.</span><span class="sxs-lookup"><span data-stu-id="d0803-212">Default variable values allow you to specify default values for variables within a template.</span></span> <span data-ttu-id="d0803-213">As variáveis padrão podem ser especificadas com as chaves que declaram a variável ou como uma coleção passada para o construtor de UriTemplate.</span><span class="sxs-lookup"><span data-stu-id="d0803-213">Default variables can be specified with the curly braces that declare the variable or as a collection passed to the UriTemplate constructor.</span></span> <span data-ttu-id="d0803-214">O modelo a seguir mostra duas maneiras de especificar um <xref:System.UriTemplate> com variáveis com valores padrão.</span><span class="sxs-lookup"><span data-stu-id="d0803-214">The following template shows two ways to specify a <xref:System.UriTemplate> with variables with default values.</span></span>  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 <span data-ttu-id="d0803-215">Este modelo declara uma variável chamada `a` com um valor padrão de `1` e uma variável chamada `b` com um valor padrão de `5` .</span><span class="sxs-lookup"><span data-stu-id="d0803-215">This template declares a variable named `a` with a default value of `1` and a variable named `b` with a default value of `5`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0803-216">Somente variáveis de segmento de caminho têm permissão para ter valores padrão.</span><span class="sxs-lookup"><span data-stu-id="d0803-216">Only path segment variables are allowed to have default values.</span></span> <span data-ttu-id="d0803-217">Variáveis de cadeia de caracteres de consulta, variáveis de segmento compostas e variáveis curinga nomeadas não têm permissão para ter valores padrão.</span><span class="sxs-lookup"><span data-stu-id="d0803-217">Query string variables, compound segment variables, and named wildcard variables are not permitted to have default values.</span></span>  
  
 <span data-ttu-id="d0803-218">O código a seguir mostra como os valores de variáveis padrão são tratados ao corresponder a um URI candidato.</span><span class="sxs-lookup"><span data-stu-id="d0803-218">The following code shows how default variable values are handled when matching a candidate URI.</span></span>  
  
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
> <span data-ttu-id="d0803-219">Um URI como não `http://localhost:8000///` corresponde ao modelo listado no código anterior, no entanto, um URI como `http://localhost:8000/` o faz.</span><span class="sxs-lookup"><span data-stu-id="d0803-219">A URI such as `http://localhost:8000///` does not match the template listed in the preceding code, however a URI such as `http://localhost:8000/` does.</span></span>  
  
 <span data-ttu-id="d0803-220">O código a seguir mostra como os valores de variáveis padrão são tratados ao criar um URI com um modelo.</span><span class="sxs-lookup"><span data-stu-id="d0803-220">The following code shows how default variable values are handled when creating a URI with a template.</span></span>  
  
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
  
<span data-ttu-id="d0803-221">Quando uma variável recebe um valor padrão, `null` há algumas restrições adicionais.</span><span class="sxs-lookup"><span data-stu-id="d0803-221">When a variable is given a default value of `null` there are some additional constraints.</span></span> <span data-ttu-id="d0803-222">Uma variável pode ter um valor padrão de `null` se a variável estiver contida no segmento mais à direita da cadeia de caracteres do modelo ou se todos os segmentos à direita do segmento tiverem valores padrão de `null` .</span><span class="sxs-lookup"><span data-stu-id="d0803-222">A variable can have a default value of `null` if the variable is contained within the right most segment of the template string or if all segments to the right of the segment have default values of `null`.</span></span> <span data-ttu-id="d0803-223">Veja a seguir as cadeias de caracteres de modelo válidas com valores padrão de `null` :</span><span class="sxs-lookup"><span data-stu-id="d0803-223">The following are valid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 <span data-ttu-id="d0803-224">Estas são as cadeias de caracteres de modelo inválidas com valores padrão de `null` :</span><span class="sxs-lookup"><span data-stu-id="d0803-224">The following are invalid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a><span data-ttu-id="d0803-225">Valores padrão e correspondência</span><span class="sxs-lookup"><span data-stu-id="d0803-225">Default Values and Matching</span></span>  
 <span data-ttu-id="d0803-226">Ao corresponder um URI candidato com um modelo que tem valores padrão, os valores padrão serão colocados na <xref:System.UriTemplateMatch.BoundVariables%2A> coleção se os valores não forem especificados no URI candidato.</span><span class="sxs-lookup"><span data-stu-id="d0803-226">When matching a candidate URI with a template that has default values, the default values are placed in the <xref:System.UriTemplateMatch.BoundVariables%2A> collection if values are not specified in the candidate URI.</span></span>  
  
### <a name="template-equivalence"></a><span data-ttu-id="d0803-227">Equivalência de modelo</span><span class="sxs-lookup"><span data-stu-id="d0803-227">Template Equivalence</span></span>  
 <span data-ttu-id="d0803-228">Dois modelos são considerados *estruturalmente equivalentes* quando todos os literais dos modelos são correspondentes e têm variáveis nos mesmos segmentos.</span><span class="sxs-lookup"><span data-stu-id="d0803-228">Two templates are said to be *structurally equivalent* when all of the templates' literals match and they have variables in the same segments.</span></span> <span data-ttu-id="d0803-229">Por exemplo, os modelos a seguir são estruturalmente equivalentes:</span><span class="sxs-lookup"><span data-stu-id="d0803-229">For example the following templates are structurally equivalent:</span></span>  
  
- <span data-ttu-id="d0803-230">/a/{var1}/b b/{var2}? x = 1&y = 2</span><span class="sxs-lookup"><span data-stu-id="d0803-230">/a/{var1}/b b/{var2}?x=1&y=2</span></span>  
  
- <span data-ttu-id="d0803-231">a/{x}/b% 20B/{var1}? y = 2&x = 1</span><span class="sxs-lookup"><span data-stu-id="d0803-231">a/{x}/b%20b/{var1}?y=2&x=1</span></span>  
  
- <span data-ttu-id="d0803-232">a/{y}/B% 20B/{z}/? y = 2&x = 1</span><span class="sxs-lookup"><span data-stu-id="d0803-232">a/{y}/B%20B/{z}/?y=2&x=1</span></span>  
  
 <span data-ttu-id="d0803-233">Algumas coisas a serem observadas:</span><span class="sxs-lookup"><span data-stu-id="d0803-233">A few things to notice:</span></span>  
  
- <span data-ttu-id="d0803-234">Se um modelo contiver barras à esquerda, somente a primeira será ignorada.</span><span class="sxs-lookup"><span data-stu-id="d0803-234">If a template contains leading slashes, only the first one is ignored.</span></span>  
  
- <span data-ttu-id="d0803-235">Ao comparar cadeias de caracteres de modelo para equivalência estrutural, Case é ignorado para nomes de variáveis e segmentos de caminho, cadeias de consulta diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="d0803-235">When comparing template strings for structural equivalence, case is ignored for variable names and path segments, query strings are case sensitive.</span></span>  
  
- <span data-ttu-id="d0803-236">As cadeias de caracteres de consulta são desordenadas.</span><span class="sxs-lookup"><span data-stu-id="d0803-236">Query strings are unordered.</span></span>  
  
## <a name="uritemplatetable"></a><span data-ttu-id="d0803-237">UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="d0803-237">UriTemplateTable</span></span>  
 <span data-ttu-id="d0803-238">A <xref:System.UriTemplateTable> classe representa uma tabela associativa de <xref:System.UriTemplate> objetos associados a um objeto da escolha do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="d0803-238">The <xref:System.UriTemplateTable> class represents an associative table of <xref:System.UriTemplate> objects bound to an object of the developer's choosing.</span></span> <span data-ttu-id="d0803-239">Um <xref:System.UriTemplateTable> deve conter pelo menos um <xref:System.UriTemplate> antes de chamar <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> .</span><span class="sxs-lookup"><span data-stu-id="d0803-239">A <xref:System.UriTemplateTable> must contain at least one <xref:System.UriTemplate> prior to calling <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span> <span data-ttu-id="d0803-240">O conteúdo de um <xref:System.UriTemplateTable> pode ser alterado até que <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> seja chamado.</span><span class="sxs-lookup"><span data-stu-id="d0803-240">The contents of a <xref:System.UriTemplateTable> can be changed until <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="d0803-241">A validação é executada quando o <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> é chamado.</span><span class="sxs-lookup"><span data-stu-id="d0803-241">Validation is performed when <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="d0803-242">O tipo de validação executada depende do valor do `allowMultiple` parâmetro para <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> .</span><span class="sxs-lookup"><span data-stu-id="d0803-242">The type of validation performed depends upon the value of the `allowMultiple` parameter to <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span>  
  
 <span data-ttu-id="d0803-243">Quando <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> o é chamado de passagem `false` , as <xref:System.UriTemplateTable> verificações para garantir que não haja modelos na tabela.</span><span class="sxs-lookup"><span data-stu-id="d0803-243">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `false`, the <xref:System.UriTemplateTable> checks to make sure there are no templates in the table.</span></span> <span data-ttu-id="d0803-244">Se encontrar qualquer modelo equivalente estrutural, ele lançará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d0803-244">If it finds any structurally equivalent templates, it throws an exception.</span></span> <span data-ttu-id="d0803-245">Isso é usado em conjunto com <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> quando você deseja garantir que apenas um modelo corresponda a um URI de entrada.</span><span class="sxs-lookup"><span data-stu-id="d0803-245">This is used in conjunction with <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> when you want to ensure only one template matches an incoming URI.</span></span>  
  
 <span data-ttu-id="d0803-246">Quando <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> o é chamado de passagem `true` , o <xref:System.UriTemplateTable> permite que vários modelos equivalentes estruturalmente estejam contidos em um <xref:System.UriTemplateTable> .</span><span class="sxs-lookup"><span data-stu-id="d0803-246">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `true`, <xref:System.UriTemplateTable> allows multiple, structurally-equivalent templates to be contained within a <xref:System.UriTemplateTable>.</span></span>  
  
 <span data-ttu-id="d0803-247">Se um conjunto de <xref:System.UriTemplate> objetos adicionado a uma <xref:System.UriTemplateTable> cadeia de caracteres de consulta contém, eles não devem ser ambíguos.</span><span class="sxs-lookup"><span data-stu-id="d0803-247">If a set of <xref:System.UriTemplate> objects added to a <xref:System.UriTemplateTable> contain query strings they must not be ambiguous.</span></span> <span data-ttu-id="d0803-248">Cadeias de caracteres de consulta idênticas são permitidas.</span><span class="sxs-lookup"><span data-stu-id="d0803-248">Identical query strings are allowed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0803-249">Embora o <xref:System.UriTemplateTable> permita endereços base que usam esquemas diferentes de http, o esquema e o número da porta são ignorados ao corresponder os URIs candidatos aos modelos.</span><span class="sxs-lookup"><span data-stu-id="d0803-249">While the <xref:System.UriTemplateTable> allows base addresses that use schemes other than HTTP, the scheme and port number are ignored when matching candidate URIs to templates.</span></span>  
  
### <a name="query-string-ambiguity"></a><span data-ttu-id="d0803-250">Ambiguidade da cadeia de caracteres de consulta</span><span class="sxs-lookup"><span data-stu-id="d0803-250">Query String Ambiguity</span></span>  
 <span data-ttu-id="d0803-251">Os modelos que compartilham um caminho equivalente contêm cadeias de caracteres de consulta ambíguas se houver um URI que corresponda a mais de um modelo.</span><span class="sxs-lookup"><span data-stu-id="d0803-251">Templates that share an equivalent path contain ambiguous query strings if there is a URI that matches more than one template.</span></span>  
  
 <span data-ttu-id="d0803-252">Os seguintes conjuntos de cadeias de caracteres de consulta não são ambíguos em si:</span><span class="sxs-lookup"><span data-stu-id="d0803-252">The following sets of query strings are unambiguous within themselves:</span></span>  
  
- <span data-ttu-id="d0803-253">? x = 1</span><span class="sxs-lookup"><span data-stu-id="d0803-253">?x=1</span></span>  
  
- <span data-ttu-id="d0803-254">? x = 2</span><span class="sxs-lookup"><span data-stu-id="d0803-254">?x=2</span></span>  
  
- <span data-ttu-id="d0803-255">? x = 3</span><span class="sxs-lookup"><span data-stu-id="d0803-255">?x=3</span></span>  
  
- <span data-ttu-id="d0803-256">? x = 1&y = {var}</span><span class="sxs-lookup"><span data-stu-id="d0803-256">?x=1&y={var}</span></span>  
  
- <span data-ttu-id="d0803-257">? x = 2&z = {var}</span><span class="sxs-lookup"><span data-stu-id="d0803-257">?x=2&z={var}</span></span>  
  
- <span data-ttu-id="d0803-258">? x = 3</span><span class="sxs-lookup"><span data-stu-id="d0803-258">?x=3</span></span>  
  
- <span data-ttu-id="d0803-259">? x = 1</span><span class="sxs-lookup"><span data-stu-id="d0803-259">?x=1</span></span>  
  
- <span data-ttu-id="d0803-260">?</span><span class="sxs-lookup"><span data-stu-id="d0803-260">?</span></span>  
  
- <span data-ttu-id="d0803-261">?</span><span class="sxs-lookup"><span data-stu-id="d0803-261">?</span></span> <span data-ttu-id="d0803-262">x = {var}</span><span class="sxs-lookup"><span data-stu-id="d0803-262">x={var}</span></span>  
  
- <span data-ttu-id="d0803-263">?</span><span class="sxs-lookup"><span data-stu-id="d0803-263">?</span></span>  
  
- <span data-ttu-id="d0803-264">? m = obter&c = RSS</span><span class="sxs-lookup"><span data-stu-id="d0803-264">?m=get&c=rss</span></span>  
  
- <span data-ttu-id="d0803-265">? m = Put&c = RSS</span><span class="sxs-lookup"><span data-stu-id="d0803-265">?m=put&c=rss</span></span>  
  
- <span data-ttu-id="d0803-266">? m = obter&c = Atom</span><span class="sxs-lookup"><span data-stu-id="d0803-266">?m=get&c=atom</span></span>  
  
- <span data-ttu-id="d0803-267">? m = Put&c = Atom</span><span class="sxs-lookup"><span data-stu-id="d0803-267">?m=put&c=atom</span></span>  
  
 <span data-ttu-id="d0803-268">Os seguintes conjuntos de modelos de cadeia de caracteres de consulta são ambíguos em si:</span><span class="sxs-lookup"><span data-stu-id="d0803-268">The following sets of query string templates are ambiguous within themselves:</span></span>  
  
- <span data-ttu-id="d0803-269">? x = 1</span><span class="sxs-lookup"><span data-stu-id="d0803-269">?x=1</span></span>  
  
- <span data-ttu-id="d0803-270">? x = {var}</span><span class="sxs-lookup"><span data-stu-id="d0803-270">?x={var}</span></span>  
  
 <span data-ttu-id="d0803-271">"x = 1"-corresponde a ambos os modelos.</span><span class="sxs-lookup"><span data-stu-id="d0803-271">"x=1" - Matches both templates.</span></span>  
  
- <span data-ttu-id="d0803-272">? x = 1</span><span class="sxs-lookup"><span data-stu-id="d0803-272">?x=1</span></span>  
  
- <span data-ttu-id="d0803-273">? y = 2</span><span class="sxs-lookup"><span data-stu-id="d0803-273">?y=2</span></span>  
  
 <span data-ttu-id="d0803-274">"x = 1&y = 2" corresponde a ambos os modelos.</span><span class="sxs-lookup"><span data-stu-id="d0803-274">"x=1&y=2" matches both templates.</span></span> <span data-ttu-id="d0803-275">Isso ocorre porque uma cadeia de caracteres de consulta pode conter mais variáveis de cadeia de caracteres de consulta que o modelo correspondente.</span><span class="sxs-lookup"><span data-stu-id="d0803-275">This is because a query string may contain more query string variables then the template it matches.</span></span>  
  
- <span data-ttu-id="d0803-276">? x = 1</span><span class="sxs-lookup"><span data-stu-id="d0803-276">?x=1</span></span>  
  
- <span data-ttu-id="d0803-277">? x = 1&y = {var}</span><span class="sxs-lookup"><span data-stu-id="d0803-277">?x=1&y={var}</span></span>  
  
 <span data-ttu-id="d0803-278">"x = 1&y = 3" corresponde a ambos os modelos.</span><span class="sxs-lookup"><span data-stu-id="d0803-278">"x=1&y=3" matches both templates.</span></span>  
  
- <span data-ttu-id="d0803-279">? x = 3&y = 4</span><span class="sxs-lookup"><span data-stu-id="d0803-279">?x=3&y=4</span></span>  
  
- <span data-ttu-id="d0803-280">? x = 3&z = 5</span><span class="sxs-lookup"><span data-stu-id="d0803-280">?x=3&z=5</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0803-281">Os caracteres á e Á são considerados caracteres diferentes quando aparecem como parte de um caminho de URI ou um <xref:System.UriTemplate> literal de segmento de caminho (mas os caracteres a e a são considerados iguais).</span><span class="sxs-lookup"><span data-stu-id="d0803-281">The characters á and Á are considered to be different characters when they appear as part of a URI path or <xref:System.UriTemplate> path segment literal (but the characters a and A are considered to be the same).</span></span> <span data-ttu-id="d0803-282">Os caracteres á e Á são considerados os mesmos caracteres quando aparecem como parte de um <xref:System.UriTemplate> {VariableName} ou uma cadeia de caracteres de consulta (e um e um também são considerados os mesmos caracteres).</span><span class="sxs-lookup"><span data-stu-id="d0803-282">The characters á and Á are considered to be the same characters when they appear as part of a <xref:System.UriTemplate> {variableName} or a query string (and a and A are also considered to be the same characters).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0803-283">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0803-283">See also</span></span>

- [<span data-ttu-id="d0803-284">Visão geral do modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="d0803-284">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="d0803-285">Modelo de objeto de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="d0803-285">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
- [<span data-ttu-id="d0803-286">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="d0803-286">UriTemplate</span></span>](../samples/uritemplate-sample.md)
- [<span data-ttu-id="d0803-287">Tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="d0803-287">UriTemplate Table</span></span>](../samples/uritemplate-table-sample.md)
- [<span data-ttu-id="d0803-288">Dispatcher de tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="d0803-288">UriTemplate Table Dispatcher</span></span>](../samples/uritemplate-table-dispatcher-sample.md)
