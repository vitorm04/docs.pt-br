---
title: UriTemplate and UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: f51d6fa5c78d97cf11a3c0005be7656013b30e90
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955278"
---
# <a name="uritemplate-and-uritemplatetable"></a><span data-ttu-id="e5ef2-102">UriTemplate and UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="e5ef2-102">UriTemplate and UriTemplateTable</span></span>
<span data-ttu-id="e5ef2-103">Os desenvolvedores da Web exigem a capacidade de descrever a forma e o layout dos URIs aos quais seus serviços respondem.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-103">Web developers require the ability to describe the shape and layout of the URIs that their services respond to.</span></span> <span data-ttu-id="e5ef2-104">Windows Communication Foundation (WCF) adicionou duas novas classes para dar aos desenvolvedores controle sobre seus URIs.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-104">Windows Communication Foundation (WCF) added two new classes to give developers control over their URIs.</span></span> <span data-ttu-id="e5ef2-105"><xref:System.UriTemplate>e <xref:System.UriTemplateTable> forma a base do mecanismo de expedição baseado em URI no WCF.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-105"><xref:System.UriTemplate> and <xref:System.UriTemplateTable> form the basis of the URI-based dispatch engine in WCF.</span></span> <span data-ttu-id="e5ef2-106">Essas classes também podem ser usadas por conta própria, permitindo que os desenvolvedores tirem proveito dos modelos e do mecanismo de mapeamento de URI sem implementar um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-106">These classes can also be used on their own, allowing developers to take advantage of templates and the URI mapping mechanism without implementing a WCF service.</span></span>  
  
## <a name="templates"></a><span data-ttu-id="e5ef2-107">Modelos</span><span class="sxs-lookup"><span data-stu-id="e5ef2-107">Templates</span></span>  
 <span data-ttu-id="e5ef2-108">Um modelo é uma maneira de descrever um conjunto de URIs relativos.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-108">A template is a way to describe a set of relative URIs.</span></span> <span data-ttu-id="e5ef2-109">O conjunto de modelos de URI na tabela a seguir mostra como um sistema que recupera vários tipos de informações de clima pode ser definido.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-109">The set of URI templates in the following table shows how a system that retrieves various types of weather information might be defined.</span></span>  
  
|<span data-ttu-id="e5ef2-110">Dados</span><span class="sxs-lookup"><span data-stu-id="e5ef2-110">Data</span></span>|<span data-ttu-id="e5ef2-111">Modelo</span><span class="sxs-lookup"><span data-stu-id="e5ef2-111">Template</span></span>|  
|----------|--------------|  
|<span data-ttu-id="e5ef2-112">Previsão nacional</span><span class="sxs-lookup"><span data-stu-id="e5ef2-112">National Forecast</span></span>|<span data-ttu-id="e5ef2-113">clima/nacional</span><span class="sxs-lookup"><span data-stu-id="e5ef2-113">weather/national</span></span>|  
|<span data-ttu-id="e5ef2-114">Previsão de estado</span><span class="sxs-lookup"><span data-stu-id="e5ef2-114">State Forecast</span></span>|<span data-ttu-id="e5ef2-115">clima/{estado}</span><span class="sxs-lookup"><span data-stu-id="e5ef2-115">weather/{state}</span></span>|  
|<span data-ttu-id="e5ef2-116">Previsão de cidade</span><span class="sxs-lookup"><span data-stu-id="e5ef2-116">City Forecast</span></span>|<span data-ttu-id="e5ef2-117">weather/{state}/{city}</span><span class="sxs-lookup"><span data-stu-id="e5ef2-117">weather/{state}/{city}</span></span>|  
|<span data-ttu-id="e5ef2-118">Previsão de atividade</span><span class="sxs-lookup"><span data-stu-id="e5ef2-118">Activity Forecast</span></span>|<span data-ttu-id="e5ef2-119">clima/{estado}/{cidade}/{atividade}</span><span class="sxs-lookup"><span data-stu-id="e5ef2-119">weather/{state}/{city}/{activity}</span></span>|  
  
 <span data-ttu-id="e5ef2-120">Esta tabela descreve um conjunto de URIs estruturalmente semelhantes.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-120">This table describes a set of structurally similar URIs.</span></span> <span data-ttu-id="e5ef2-121">Cada entrada é um modelo de URI.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-121">Each entry is a URI template.</span></span> <span data-ttu-id="e5ef2-122">Os segmentos entre chaves descrevem as variáveis.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-122">The segments in curly braces describe variables.</span></span> <span data-ttu-id="e5ef2-123">Os segmentos que não estão entre chaves descrevem cadeias de caracteres literais.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-123">The segments not in curly braces describe literal strings.</span></span> <span data-ttu-id="e5ef2-124">As classes de modelo do WCF permitem que um desenvolvedor Use um URI de entrada, por exemplo, "/Weather/wa/Seattle/Cycling" e faça a correspondência com um modelo que o descreva, "/Weather/{State}/{City}/{Activity}".</span><span class="sxs-lookup"><span data-stu-id="e5ef2-124">The WCF template classes allow a developer to take an incoming URI, for example, "/weather/wa/seattle/cycling", and match it to a template that describes it, "/weather/{state}/{city}/{activity}".</span></span>  
  
## <a name="uritemplate"></a><span data-ttu-id="e5ef2-125">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="e5ef2-125">UriTemplate</span></span>  
 <span data-ttu-id="e5ef2-126"><xref:System.UriTemplate>é uma classe que encapsula um modelo de URI.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-126"><xref:System.UriTemplate> is a class that encapsulates a URI template.</span></span> <span data-ttu-id="e5ef2-127">O construtor usa um parâmetro de cadeia de caracteres que define o modelo.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-127">The constructor takes a string parameter that defines the template.</span></span> <span data-ttu-id="e5ef2-128">Essa cadeia de caracteres contém o modelo no formato descrito na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-128">This string contains the template in the format described in the next section.</span></span> <span data-ttu-id="e5ef2-129">A <xref:System.UriTemplate> classe fornece métodos que permitem que você corresponda a um URI de entrada para um modelo, gere um URI a partir de um modelo, recupere uma coleção de nomes de variáveis usados no modelo, determine se dois modelos são equivalentes e retorne o Strings.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-129">The <xref:System.UriTemplate> class provides methods that allow you match an incoming URI to a template, generate a URI from a template, retrieve a collection of variable names used in the template, determine whether two templates are equivalent, and return the template's string.</span></span>  
  
 <span data-ttu-id="e5ef2-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29>usa um endereço base e um URI candidato e tenta corresponder o URI ao modelo.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> takes a base address and a candidate URI and attempts to match the URI to the template.</span></span> <span data-ttu-id="e5ef2-131">Se a correspondência for bem-sucedida, uma <xref:System.UriTemplateMatch> instância será retornada.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-131">If the match is successful, a <xref:System.UriTemplateMatch> instance is returned.</span></span> <span data-ttu-id="e5ef2-132">O <xref:System.UriTemplateMatch> objeto contém um URI base, o URI candidato, uma coleção de nome/valor dos parâmetros de consulta, uma matriz dos segmentos de caminho relativo, uma coleção de nome/valor de variáveis que foram correspondidas, a <xref:System.UriTemplate> instância usada para executar a correspondência , uma cadeia de caracteres que contém qualquer parte não correspondente do URI candidato (usada quando o modelo tem um caractere curinga) e um objeto associado ao modelo.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-132">The <xref:System.UriTemplateMatch> object contains a base URI, the candidate URI, a name/value collection of the query parameters, an array of the relative path segments, a name/value collection of variables that were matched, the <xref:System.UriTemplate> instance used to perform the match, a string that contains any unmatched portion of the candidate URI (used when the template has a wildcard), and an object that is associated with the template.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5ef2-133">A <xref:System.UriTemplate> classe ignora o esquema e o número da porta ao corresponder um URI candidato a um modelo.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-133">The <xref:System.UriTemplate> class ignores the scheme and port number when matching a candidate URI to a template.</span></span>  
  
 <span data-ttu-id="e5ef2-134">Há dois métodos que permitem gerar um URI a partir de um modelo <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> e. <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29></span><span class="sxs-lookup"><span data-stu-id="e5ef2-134">There are two methods that allow you to generate a URI from a template, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> and <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span></span> <span data-ttu-id="e5ef2-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29>usa um endereço base e uma coleção de nome/valor de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> takes a base address and a name/value collection of parameters.</span></span> <span data-ttu-id="e5ef2-136">Esses parâmetros são substituídos por variáveis quando o modelo é associado.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-136">These parameters are substituted for variables when the template is bound.</span></span> <span data-ttu-id="e5ef2-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>usa os pares de nome/valor e os substitui da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> takes the name/value pairs and substitutes them left to right.</span></span>  
  
 <span data-ttu-id="e5ef2-138"><xref:System.UriTemplate.ToString>Retorna a cadeia de caracteres do modelo.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-138"><xref:System.UriTemplate.ToString> returns the template string.</span></span>  
  
 <span data-ttu-id="e5ef2-139">A <xref:System.UriTemplate.PathSegmentVariableNames%2A> propriedade contém uma coleção dos nomes das variáveis usadas em segmentos de caminho na cadeia de caracteres do modelo.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-139">The <xref:System.UriTemplate.PathSegmentVariableNames%2A> property contains a collection of the names of the variables used within path segments in the template string.</span></span>  
  
 <span data-ttu-id="e5ef2-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29>usa um <xref:System.UriTemplate> como parâmetro e retorna um valor booliano que especifica se os dois modelos são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> takes a <xref:System.UriTemplate> as a parameter and returns a Boolean value that specifies whether the two templates are equivalent.</span></span> <span data-ttu-id="e5ef2-141">Para obter mais informações, consulte a seção equivalência de modelo mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-141">For more information, see the Template Equivalence section later in this topic.</span></span>  
  
 <span data-ttu-id="e5ef2-142"><xref:System.UriTemplate>foi projetado para funcionar com qualquer esquema URI que esteja de acordo com a gramática de HTTP URI.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-142"><xref:System.UriTemplate> is designed to work with any URI scheme that conforms to the HTTP URI grammar.</span></span> <span data-ttu-id="e5ef2-143">Veja a seguir exemplos de esquemas de URI com suporte.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-143">The following are examples of supported URI schemes.</span></span>  
  
- <span data-ttu-id="e5ef2-144">http://</span><span class="sxs-lookup"><span data-stu-id="e5ef2-144">http://</span></span>  
  
- <span data-ttu-id="e5ef2-145">https://</span><span class="sxs-lookup"><span data-stu-id="e5ef2-145">https://</span></span>  
  
- <span data-ttu-id="e5ef2-146">net.tcp://</span><span class="sxs-lookup"><span data-stu-id="e5ef2-146">net.tcp://</span></span>  
  
- <span data-ttu-id="e5ef2-147">net.pipe://</span><span class="sxs-lookup"><span data-stu-id="e5ef2-147">net.pipe://</span></span>  
  
- <span data-ttu-id="e5ef2-148">sb://</span><span class="sxs-lookup"><span data-stu-id="e5ef2-148">sb://</span></span>  
  
 <span data-ttu-id="e5ef2-149">Esquemas como file://e urn://não estão em conformidade com a gramática de HTTP URI e causam resultados imprevisíveis quando usados com modelos de URI.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-149">Schemes like file:// and urn:// do not conform to the HTTP URI grammar and cause unpredictable results when used with URI templates.</span></span>  
  
### <a name="template-string-syntax"></a><span data-ttu-id="e5ef2-150">Sintaxe de cadeia de caracteres de modelo</span><span class="sxs-lookup"><span data-stu-id="e5ef2-150">Template String Syntax</span></span>  
 <span data-ttu-id="e5ef2-151">Um modelo tem três partes: um caminho, uma consulta opcional e um fragmento opcional.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-151">A template has three parts: a path, an optional query, and an optional fragment.</span></span> <span data-ttu-id="e5ef2-152">Para obter um exemplo, consulte o seguinte modelo:</span><span class="sxs-lookup"><span data-stu-id="e5ef2-152">For an example, see the following template:</span></span>  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 <span data-ttu-id="e5ef2-153">O caminho consiste em "/Weather/{State}/{City}", a consulta consiste em "? previsão = {Length} e o fragmento consiste em" #frag1 ".</span><span class="sxs-lookup"><span data-stu-id="e5ef2-153">The path consists of "/weather/{state}/{city}", the query consists of "?forecast={length}, and the fragment consists of "#frag1".</span></span>  
  
 <span data-ttu-id="e5ef2-154">As barras à esquerda e à direita são opcionais na expressão de caminho.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-154">Leading and trailing slashes are optional in the path expression.</span></span> <span data-ttu-id="e5ef2-155">Tanto as expressões de consulta quanto de fragmento podem ser omitidas inteiramente.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-155">Both the query and fragment expressions can be omitted entirely.</span></span> <span data-ttu-id="e5ef2-156">Um caminho consiste em uma série de segmentos delimitados por '/', cada segmento pode ter um valor literal, um nome de variável (escrito em {keycolchetes}) ou um curinga (gravado como\*' ').</span><span class="sxs-lookup"><span data-stu-id="e5ef2-156">A path consists of a series of segments delimited by '/', each segment can have a literal value, a variable name (written in {curly braces}), or a wildcard (written as '\*').</span></span> <span data-ttu-id="e5ef2-157">No modelo anterior, o "segmento \weather\ é um valor literal enquanto" {State} "e" {City} "são variáveis.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-157">In the previous template the "\weather\ segment is a literal value while "{state}" and "{city}" are variables.</span></span> <span data-ttu-id="e5ef2-158">As variáveis recebem seu nome do conteúdo de suas chaves e elas podem ser substituídas posteriormente por um valor concreto para criar um *URI fechado*.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-158">Variables take their name from the contents of their curly braces and they can later be replaced with a concrete value to create a *closed URI*.</span></span> <span data-ttu-id="e5ef2-159">O curinga é opcional, mas só pode aparecer no final do URI, onde ele corresponde logicamente a "o restante do caminho".</span><span class="sxs-lookup"><span data-stu-id="e5ef2-159">The wildcard is optional, but can only appear at the end of the URI, where it logically matches "the rest of the path".</span></span>  
  
 <span data-ttu-id="e5ef2-160">A expressão de consulta, se presente, especifica uma série de pares de nome/valor não ordenados delimitadas por ' & '.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-160">The query expression, if present, specifies a series of unordered name/value pairs delimited by '&'.</span></span> <span data-ttu-id="e5ef2-161">Os elementos da expressão de consulta podem ser pares literais (x = 2) ou um par de variáveis (x = {var}).</span><span class="sxs-lookup"><span data-stu-id="e5ef2-161">Elements of the query expression can either be literal pairs (x=2) or a variable pair (x={var}).</span></span> <span data-ttu-id="e5ef2-162">Somente o lado direito da consulta pode ter uma expressão variável.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-162">Only the right side of the query can have a variable expression.</span></span> <span data-ttu-id="e5ef2-163">({somename} = {someValue} não é permitido.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-163">({someName} = {someValue} is not allowed.</span></span> <span data-ttu-id="e5ef2-164">Valores não emparelhados (? x) não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-164">Unpaired values (?x) are not permitted.</span></span> <span data-ttu-id="e5ef2-165">Não há nenhuma diferença entre uma expressão de consulta vazia e uma expressão de consulta consistindo apenas em um único '? ' (ambos significam "qualquer consulta").</span><span class="sxs-lookup"><span data-stu-id="e5ef2-165">There is no difference between an empty query expression and a query expression consisting of just a single '?' (both mean "any query").</span></span>  
  
 <span data-ttu-id="e5ef2-166">A expressão de fragmento pode consistir em um valor literal, nenhuma variável é permitida.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-166">The fragment expression can consist of a literal value, no variables are allowed.</span></span>  
  
 <span data-ttu-id="e5ef2-167">Todos os nomes de variáveis de modelo dentro de uma cadeia de caracteres de modelo devem ser exclusivos.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-167">All template variable names within a template string must be unique.</span></span> <span data-ttu-id="e5ef2-168">Os nomes de variáveis de modelo não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-168">Template variable names are case-insensitive.</span></span>  
  
 <span data-ttu-id="e5ef2-169">Exemplos de cadeias de caracteres de modelo válidas:</span><span class="sxs-lookup"><span data-stu-id="e5ef2-169">Examples of valid template strings:</span></span>  
  
- <span data-ttu-id="e5ef2-170">""</span><span class="sxs-lookup"><span data-stu-id="e5ef2-170">""</span></span>  
  
- <span data-ttu-id="e5ef2-171">"/shoe"</span><span class="sxs-lookup"><span data-stu-id="e5ef2-171">"/shoe"</span></span>  
  
- <span data-ttu-id="e5ef2-172">"/Shoe/\*"</span><span class="sxs-lookup"><span data-stu-id="e5ef2-172">"/shoe/\*"</span></span>  
  
- <span data-ttu-id="e5ef2-173">"{sapato}/Boat"</span><span class="sxs-lookup"><span data-stu-id="e5ef2-173">"{shoe}/boat"</span></span>  
  
- <span data-ttu-id="e5ef2-174">"{sapato}/{Boat}/Bed/{Quilt}"</span><span class="sxs-lookup"><span data-stu-id="e5ef2-174">"{shoe}/{boat}/bed/{quilt}"</span></span>  
  
- <span data-ttu-id="e5ef2-175">"sapato/{barco}"</span><span class="sxs-lookup"><span data-stu-id="e5ef2-175">"shoe/{boat}"</span></span>  
  
- <span data-ttu-id="e5ef2-176">"sapato/{barco}/\*"</span><span class="sxs-lookup"><span data-stu-id="e5ef2-176">"shoe/{boat}/\*"</span></span>  
  
- <span data-ttu-id="e5ef2-177">"sapato/barco? x = 2"</span><span class="sxs-lookup"><span data-stu-id="e5ef2-177">"shoe/boat?x=2"</span></span>  
  
- <span data-ttu-id="e5ef2-178">"shoe/{boat}?x={bed}"</span><span class="sxs-lookup"><span data-stu-id="e5ef2-178">"shoe/{boat}?x={bed}"</span></span>  
  
- <span data-ttu-id="e5ef2-179">"shoe/{boat}?x={bed}&y=band"</span><span class="sxs-lookup"><span data-stu-id="e5ef2-179">"shoe/{boat}?x={bed}&y=band"</span></span>  
  
- <span data-ttu-id="e5ef2-180">"?x={shoe}"</span><span class="sxs-lookup"><span data-stu-id="e5ef2-180">"?x={shoe}"</span></span>  
  
- <span data-ttu-id="e5ef2-181">"sapato? x = 3 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="e5ef2-181">"shoe?x=3&y={var}</span></span>  
  
 <span data-ttu-id="e5ef2-182">Exemplos de cadeias de caracteres de modelo inválidas:</span><span class="sxs-lookup"><span data-stu-id="e5ef2-182">Examples of invalid template strings:</span></span>  
  
- <span data-ttu-id="e5ef2-183">"{sapato}/{SHOE}/x = 2" – nomes de variáveis duplicados.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-183">"{shoe}/{SHOE}/x=2" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="e5ef2-184">"{sapato}/Boat/? cama = {sapato}" – nomes de variáveis duplicados.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-184">"{shoe}/boat/?bed={shoe}" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="e5ef2-185">"? x = 2 & x = 3" – os pares de nome/valor dentro de uma cadeia de caracteres de consulta devem ser exclusivos, mesmo que sejam literais.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-185">"?x=2&x=3" – Name/value pairs within a query string must be unique, even if they are literals.</span></span>  
  
- <span data-ttu-id="e5ef2-186">"? x = 2 &" – a cadeia de caracteres de consulta está malformada.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-186">"?x=2&" – Query string is malformed.</span></span>  
  
- <span data-ttu-id="e5ef2-187">"? 2 & x = {sapato}" – a cadeia de caracteres de consulta deve ser pares de nome/valor.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-187">"?2&x={shoe}" – Query string must be name/value pairs.</span></span>  
  
- <span data-ttu-id="e5ef2-188">"? y = 2 & & X = 3" – a cadeia de caracteres de consulta deve ser pares de valores de nome, os nomes não podem começar com ' & '.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-188">"?y=2&&X=3" – Query string must be name value pairs, names cannot start with '&'.</span></span>  
  
### <a name="compound-path-segments"></a><span data-ttu-id="e5ef2-189">Segmentos de caminho composto</span><span class="sxs-lookup"><span data-stu-id="e5ef2-189">Compound Path Segments</span></span>  
 <span data-ttu-id="e5ef2-190">Segmentos de caminho composto permitem que um único segmento de caminho de URI contenha várias variáveis, bem como variáveis combinadas com literais.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-190">Compound path segments allow a single URI path segment to contain multiple variables as well as variables combined with literals.</span></span> <span data-ttu-id="e5ef2-191">Veja a seguir exemplos de segmentos de caminho composto válidos.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-191">The following are examples of valid compound path segments.</span></span>  
  
- <span data-ttu-id="e5ef2-192">/filename.{ext}/</span><span class="sxs-lookup"><span data-stu-id="e5ef2-192">/filename.{ext}/</span></span>  
  
- <span data-ttu-id="e5ef2-193">/{filename}.jpg/</span><span class="sxs-lookup"><span data-stu-id="e5ef2-193">/{filename}.jpg/</span></span>  
  
- <span data-ttu-id="e5ef2-194">/{filename}.{ext}/</span><span class="sxs-lookup"><span data-stu-id="e5ef2-194">/{filename}.{ext}/</span></span>  
  
- <span data-ttu-id="e5ef2-195">um. {b} someLiteral {c} ({d})/</span><span class="sxs-lookup"><span data-stu-id="e5ef2-195">/{a}.{b}someLiteral{c}({d})/</span></span>  
  
 <span data-ttu-id="e5ef2-196">Veja a seguir exemplos de segmentos de caminho inválidos.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-196">The following are examples of invalid path segments.</span></span>  
  
- <span data-ttu-id="e5ef2-197">As{} variáveis/devem ser nomeadas.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-197">/{} - Variables must be named.</span></span>  
  
- <span data-ttu-id="e5ef2-198">/{Shoe}{Boat}-as variáveis devem ser separadas por um literal.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-198">/{shoe}{boat} - Variables must be separated by a literal.</span></span>  
  
### <a name="matching-and-compound-path-segments"></a><span data-ttu-id="e5ef2-199">Correspondência e segmentos de caminho compostos</span><span class="sxs-lookup"><span data-stu-id="e5ef2-199">Matching and Compound Path Segments</span></span>  
 <span data-ttu-id="e5ef2-200">Segmentos de caminho composto permitem que você defina um UriTemplate que tenha várias variáveis dentro de um único segmento de caminho.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-200">Compound path segments allow you to define a UriTemplate that has multiple variables within a single path segment.</span></span> <span data-ttu-id="e5ef2-201">Por exemplo, na seguinte cadeia de caracteres de modelo: "Addresses/{State}. {City} "duas variáveis (State e City) são definidas dentro do mesmo segmento.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-201">For example, in the following template string: "Addresses/{state}.{city}" two variables (state and city) are defined within the same segment.</span></span> <span data-ttu-id="e5ef2-202">Esse modelo corresponderia a uma URL `http://example.com/Washington.Redmond` como, mas também corresponderá a `http://example.com/Washington.Redmond.Microsoft`uma URL como.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-202">This template would match a URL such as `http://example.com/Washington.Redmond` but it will also match an URL like `http://example.com/Washington.Redmond.Microsoft`.</span></span> <span data-ttu-id="e5ef2-203">No último caso, a variável de estado conterá "Washington" e a variável City conterá "Redmond. Microsoft".</span><span class="sxs-lookup"><span data-stu-id="e5ef2-203">In the latter case, the state variable will contain "Washington" and the city variable will contain "Redmond.Microsoft".</span></span> <span data-ttu-id="e5ef2-204">Nesse caso, qualquer texto (exceto '/') corresponderá à variável {City}.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-204">In this case any text (except ‘/’) will match the {city} variable.</span></span> <span data-ttu-id="e5ef2-205">Se você quiser um modelo que não corresponda ao texto "extra", coloque a variável em um segmento de modelo separado, por exemplo: "Addresses/{State}/{City}.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-205">If you want a template that will not match the "extra" text, place the variable in a separate template segment, for example: "Addresses/{state}/{city}.</span></span>  
  
### <a name="named-wildcard-segments"></a><span data-ttu-id="e5ef2-206">Segmentos curinga nomeados</span><span class="sxs-lookup"><span data-stu-id="e5ef2-206">Named Wildcard Segments</span></span>  
 <span data-ttu-id="e5ef2-207">Um segmento curinga nomeado é qualquer segmento de variável de caminho cujo nome da variável comece com o\*caractere curinga ' '.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-207">A named wildcard segment is any path variable segment whose variable name begins with the wildcard character ‘\*’.</span></span> <span data-ttu-id="e5ef2-208">A cadeia de caracteres de modelo a seguir contém um segmento curinga nomeado chamado "sapato".</span><span class="sxs-lookup"><span data-stu-id="e5ef2-208">The following template string contains a named wildcard segment named "shoe".</span></span>  
  
```  
"literal/{*shoe}"  
```  
  
 <span data-ttu-id="e5ef2-209">Os segmentos curinga devem seguir as seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="e5ef2-209">Wildcard segments must follow the following rules:</span></span>  
  
- <span data-ttu-id="e5ef2-210">Pode haver no máximo um segmento curinga nomeado para cada cadeia de caracteres de modelo.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-210">There can be at most one named wildcard segment for each template string.</span></span>  
  
- <span data-ttu-id="e5ef2-211">Um segmento curinga nomeado deve aparecer no segmento mais à direita no caminho.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-211">A named wildcard segment must appear at the right-most segment in the path.</span></span>  
  
- <span data-ttu-id="e5ef2-212">Um segmento curinga nomeado não pode coexistir com um segmento curinga anônimo dentro da mesma cadeia de caracteres de modelo.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-212">A named wildcard segment cannot coexist with an anonymous wildcard segment within the same template string.</span></span>  
  
- <span data-ttu-id="e5ef2-213">O nome de um segmento curinga nomeado deve ser exclusivo.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-213">The name of a named wildcard segment must be unique.</span></span>  
  
- <span data-ttu-id="e5ef2-214">Segmentos curinga nomeados não podem ter valores padrão.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-214">Named wildcard segments cannot have default values.</span></span>  
  
- <span data-ttu-id="e5ef2-215">Segmentos curinga nomeados não podem terminar com "/".</span><span class="sxs-lookup"><span data-stu-id="e5ef2-215">Named wildcard segments cannot end with "/".</span></span>  
  
### <a name="default-variable-values"></a><span data-ttu-id="e5ef2-216">Valores de variáveis padrão</span><span class="sxs-lookup"><span data-stu-id="e5ef2-216">Default Variable Values</span></span>  
 <span data-ttu-id="e5ef2-217">Valores de variáveis padrão permitem que você especifique valores padrão para variáveis dentro de um modelo.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-217">Default variable values allow you to specify default values for variables within a template.</span></span> <span data-ttu-id="e5ef2-218">As variáveis padrão podem ser especificadas com as chaves que declaram a variável ou como uma coleção passada para o construtor de UriTemplate.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-218">Default variables can be specified with the curly braces that declare the variable or as a collection passed to the UriTemplate constructor.</span></span> <span data-ttu-id="e5ef2-219">O modelo a seguir mostra duas maneiras de especificar <xref:System.UriTemplate> um com variáveis com valores padrão.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-219">The following template shows two ways to specify a <xref:System.UriTemplate> with variables with default values.</span></span>  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 <span data-ttu-id="e5ef2-220">Este modelo declara `a` uma variável chamada com um valor padrão de `1` e uma variável chamada `b` com um valor padrão de `5`.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-220">This template declares a variable named `a` with a default value of `1` and a variable named `b` with a default value of `5`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5ef2-221">Somente variáveis de segmento de caminho têm permissão para ter valores padrão.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-221">Only path segment variables are allowed to have default values.</span></span> <span data-ttu-id="e5ef2-222">Variáveis de cadeia de caracteres de consulta, variáveis de segmento compostas e variáveis curinga nomeadas não têm permissão para ter valores padrão.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-222">Query string variables, compound segment variables, and named wildcard variables are not permitted to have default values.</span></span>  
  
 <span data-ttu-id="e5ef2-223">O código a seguir mostra como os valores de variáveis padrão são tratados ao corresponder a um URI candidato.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-223">The following code shows how default variable values are handled when matching a candidate URI.</span></span>  
  
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
> <span data-ttu-id="e5ef2-224">Um URI como `http://localhost:8000///` não corresponde ao modelo listado no código anterior, no entanto, um URI `http://localhost:8000/` como o faz.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-224">A URI such as `http://localhost:8000///` does not match the template listed in the preceding code, however a URI such as `http://localhost:8000/` does.</span></span>  
  
 <span data-ttu-id="e5ef2-225">O código a seguir mostra como os valores de variáveis padrão são tratados ao criar um URI com um modelo.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-225">The following code shows how default variable values are handled when creating a URI with a template.</span></span>  
  
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
  
<span data-ttu-id="e5ef2-226">Quando uma variável recebe um valor `null` padrão, há algumas restrições adicionais.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-226">When a variable is given a default value of `null` there are some additional constraints.</span></span> <span data-ttu-id="e5ef2-227">Uma variável pode ter um valor padrão de `null` se a variável estiver contida no segmento mais à direita da cadeia de caracteres do modelo ou se todos os segmentos à direita do segmento tiverem valores padrão `null`de.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-227">A variable can have a default value of `null` if the variable is contained within the right most segment of the template string or if all segments to the right of the segment have default values of `null`.</span></span> <span data-ttu-id="e5ef2-228">Veja a seguir as cadeias de caracteres de modelo `null`válidas com valores padrão de:</span><span class="sxs-lookup"><span data-stu-id="e5ef2-228">The following are valid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 <span data-ttu-id="e5ef2-229">Estas são as cadeias de caracteres de modelo inválidas com valores padrão de `null`:</span><span class="sxs-lookup"><span data-stu-id="e5ef2-229">The following are invalid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a><span data-ttu-id="e5ef2-230">Valores padrão e correspondência</span><span class="sxs-lookup"><span data-stu-id="e5ef2-230">Default Values and Matching</span></span>  
 <span data-ttu-id="e5ef2-231">Ao corresponder um URI candidato com um modelo que tem valores padrão, os valores padrão serão colocados na <xref:System.UriTemplateMatch.BoundVariables%2A> coleção se os valores não forem especificados no URI candidato.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-231">When matching a candidate URI with a template that has default values, the default values are placed in the <xref:System.UriTemplateMatch.BoundVariables%2A> collection if values are not specified in the candidate URI.</span></span>  
  
### <a name="template-equivalence"></a><span data-ttu-id="e5ef2-232">Equivalência de modelo</span><span class="sxs-lookup"><span data-stu-id="e5ef2-232">Template Equivalence</span></span>  
 <span data-ttu-id="e5ef2-233">Dois modelos são considerados estruturalmente *equivalentes* quando todos os literais dos modelos são correspondentes e têm variáveis nos mesmos segmentos.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-233">Two templates are said to be *structurally equivalent* when all of the templates' literals match and they have variables in the same segments.</span></span> <span data-ttu-id="e5ef2-234">Por exemplo, os modelos a seguir são estruturalmente equivalentes:</span><span class="sxs-lookup"><span data-stu-id="e5ef2-234">For example the following templates are structurally equivalent:</span></span>  
  
- <span data-ttu-id="e5ef2-235">/a/{var1}/b b/{var2}?x=1&y=2</span><span class="sxs-lookup"><span data-stu-id="e5ef2-235">/a/{var1}/b b/{var2}?x=1&y=2</span></span>  
  
- <span data-ttu-id="e5ef2-236">a/{x}/b% 20B/{var1}? y = 2 & x = 1</span><span class="sxs-lookup"><span data-stu-id="e5ef2-236">a/{x}/b%20b/{var1}?y=2&x=1</span></span>  
  
- <span data-ttu-id="e5ef2-237">a/{y}/B%20B/{z}/?y=2&x=1</span><span class="sxs-lookup"><span data-stu-id="e5ef2-237">a/{y}/B%20B/{z}/?y=2&x=1</span></span>  
  
 <span data-ttu-id="e5ef2-238">Algumas coisas a serem observadas:</span><span class="sxs-lookup"><span data-stu-id="e5ef2-238">A few things to notice:</span></span>  
  
- <span data-ttu-id="e5ef2-239">Se um modelo contiver barras à esquerda, somente a primeira será ignorada.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-239">If a template contains leading slashes, only the first one is ignored.</span></span>  
  
- <span data-ttu-id="e5ef2-240">Ao comparar cadeias de caracteres de modelo para equivalência estrutural, Case é ignorado para nomes de variáveis e segmentos de caminho, cadeias de consulta diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-240">When comparing template strings for structural equivalence, case is ignored for variable names and path segments, query strings are case sensitive.</span></span>  
  
- <span data-ttu-id="e5ef2-241">As cadeias de caracteres de consulta são desordenadas.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-241">Query strings are unordered.</span></span>  
  
## <a name="uritemplatetable"></a><span data-ttu-id="e5ef2-242">UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="e5ef2-242">UriTemplateTable</span></span>  
 <span data-ttu-id="e5ef2-243">A <xref:System.UriTemplateTable> classe representa uma tabela associativa de <xref:System.UriTemplate> objetos associados a um objeto da escolha do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-243">The <xref:System.UriTemplateTable> class represents an associative table of <xref:System.UriTemplate> objects bound to an object of the developer's choosing.</span></span> <span data-ttu-id="e5ef2-244">Um <xref:System.UriTemplateTable> deve conter pelo menos um <xref:System.UriTemplate> antes de chamar <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-244">A <xref:System.UriTemplateTable> must contain at least one <xref:System.UriTemplate> prior to calling <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span> <span data-ttu-id="e5ef2-245">O conteúdo de um <xref:System.UriTemplateTable> pode ser alterado até <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> que seja chamado.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-245">The contents of a <xref:System.UriTemplateTable> can be changed until <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="e5ef2-246">A validação é executada <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> quando o é chamado.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-246">Validation is performed when <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="e5ef2-247">O tipo de validação executada depende do valor do `allowMultiple` parâmetro para. <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29></span><span class="sxs-lookup"><span data-stu-id="e5ef2-247">The type of validation performed depends upon the value of the `allowMultiple` parameter to <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span>  
  
 <span data-ttu-id="e5ef2-248">Quando <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> o é chamado de `false`passagem, <xref:System.UriTemplateTable> as verificações para garantir que não haja modelos na tabela.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-248">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `false`, the <xref:System.UriTemplateTable> checks to make sure there are no templates in the table.</span></span> <span data-ttu-id="e5ef2-249">Se encontrar qualquer modelo equivalente estrutural, ele lançará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-249">If it finds any structurally equivalent templates, it throws an exception.</span></span> <span data-ttu-id="e5ef2-250">Isso é usado em conjunto com <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> quando você deseja garantir que apenas um modelo corresponda a um URI de entrada.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-250">This is used in conjunction with <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> when you want to ensure only one template matches an incoming URI.</span></span>  
  
 <span data-ttu-id="e5ef2-251">Quando <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> o é chamado de `true`passagem <xref:System.UriTemplateTable> , o permite que vários modelos equivalentes estruturalmente estejam contidos em <xref:System.UriTemplateTable>um.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-251">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `true`, <xref:System.UriTemplateTable> allows multiple, structurally-equivalent templates to be contained within a <xref:System.UriTemplateTable>.</span></span>  
  
 <span data-ttu-id="e5ef2-252">Se um conjunto de <xref:System.UriTemplate> objetos adicionado a uma <xref:System.UriTemplateTable> cadeia de caracteres de consulta contém, eles não devem ser ambíguos.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-252">If a set of <xref:System.UriTemplate> objects added to a <xref:System.UriTemplateTable> contain query strings they must not be ambiguous.</span></span> <span data-ttu-id="e5ef2-253">Cadeias de caracteres de consulta idênticas são permitidas.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-253">Identical query strings are allowed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5ef2-254">Embora o <xref:System.UriTemplateTable> permita endereços base que usam esquemas diferentes de http, o esquema e o número da porta são ignorados ao corresponder os URIs candidatos aos modelos.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-254">While the <xref:System.UriTemplateTable> allows base addresses that use schemes other than HTTP, the scheme and port number are ignored when matching candidate URIs to templates.</span></span>  
  
### <a name="query-string-ambiguity"></a><span data-ttu-id="e5ef2-255">Ambiguidade da cadeia de caracteres de consulta</span><span class="sxs-lookup"><span data-stu-id="e5ef2-255">Query String Ambiguity</span></span>  
 <span data-ttu-id="e5ef2-256">Os modelos que compartilham um caminho equivalente contêm cadeias de caracteres de consulta ambíguas se houver um URI que corresponda a mais de um modelo.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-256">Templates that share an equivalent path contain ambiguous query strings if there is a URI that matches more than one template.</span></span>  
  
 <span data-ttu-id="e5ef2-257">Os seguintes conjuntos de cadeias de caracteres de consulta não são ambíguos em si:</span><span class="sxs-lookup"><span data-stu-id="e5ef2-257">The following sets of query strings are unambiguous within themselves:</span></span>  
  
- <span data-ttu-id="e5ef2-258">?x=1</span><span class="sxs-lookup"><span data-stu-id="e5ef2-258">?x=1</span></span>  
  
- <span data-ttu-id="e5ef2-259">?x=2</span><span class="sxs-lookup"><span data-stu-id="e5ef2-259">?x=2</span></span>  
  
- <span data-ttu-id="e5ef2-260">?x=3</span><span class="sxs-lookup"><span data-stu-id="e5ef2-260">?x=3</span></span>  
  
- <span data-ttu-id="e5ef2-261">?x=1&y={var}</span><span class="sxs-lookup"><span data-stu-id="e5ef2-261">?x=1&y={var}</span></span>  
  
- <span data-ttu-id="e5ef2-262">?x=2&z={var}</span><span class="sxs-lookup"><span data-stu-id="e5ef2-262">?x=2&z={var}</span></span>  
  
- <span data-ttu-id="e5ef2-263">?x=3</span><span class="sxs-lookup"><span data-stu-id="e5ef2-263">?x=3</span></span>  
  
- <span data-ttu-id="e5ef2-264">?x=1</span><span class="sxs-lookup"><span data-stu-id="e5ef2-264">?x=1</span></span>  
  
- <span data-ttu-id="e5ef2-265">?</span><span class="sxs-lookup"><span data-stu-id="e5ef2-265">?</span></span>  
  
- <span data-ttu-id="e5ef2-266">?</span><span class="sxs-lookup"><span data-stu-id="e5ef2-266">?</span></span> <span data-ttu-id="e5ef2-267">x={var}</span><span class="sxs-lookup"><span data-stu-id="e5ef2-267">x={var}</span></span>  
  
- <span data-ttu-id="e5ef2-268">?</span><span class="sxs-lookup"><span data-stu-id="e5ef2-268">?</span></span>  
  
- <span data-ttu-id="e5ef2-269">?m=get&c=rss</span><span class="sxs-lookup"><span data-stu-id="e5ef2-269">?m=get&c=rss</span></span>  
  
- <span data-ttu-id="e5ef2-270">? m = Put & c = RSS</span><span class="sxs-lookup"><span data-stu-id="e5ef2-270">?m=put&c=rss</span></span>  
  
- <span data-ttu-id="e5ef2-271">?m=get&c=atom</span><span class="sxs-lookup"><span data-stu-id="e5ef2-271">?m=get&c=atom</span></span>  
  
- <span data-ttu-id="e5ef2-272">? m = Put & c = Atom</span><span class="sxs-lookup"><span data-stu-id="e5ef2-272">?m=put&c=atom</span></span>  
  
 <span data-ttu-id="e5ef2-273">Os seguintes conjuntos de modelos de cadeia de caracteres de consulta são ambíguos em si:</span><span class="sxs-lookup"><span data-stu-id="e5ef2-273">The following sets of query string templates are ambiguous within themselves:</span></span>  
  
- <span data-ttu-id="e5ef2-274">?x=1</span><span class="sxs-lookup"><span data-stu-id="e5ef2-274">?x=1</span></span>  
  
- <span data-ttu-id="e5ef2-275">?x={var}</span><span class="sxs-lookup"><span data-stu-id="e5ef2-275">?x={var}</span></span>  
  
 <span data-ttu-id="e5ef2-276">"x = 1"-corresponde a ambos os modelos.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-276">"x=1" - Matches both templates.</span></span>  
  
- <span data-ttu-id="e5ef2-277">?x=1</span><span class="sxs-lookup"><span data-stu-id="e5ef2-277">?x=1</span></span>  
  
- <span data-ttu-id="e5ef2-278">?y=2</span><span class="sxs-lookup"><span data-stu-id="e5ef2-278">?y=2</span></span>  
  
 <span data-ttu-id="e5ef2-279">"x = 1 & y = 2" corresponde a ambos os modelos.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-279">"x=1&y=2" matches both templates.</span></span> <span data-ttu-id="e5ef2-280">Isso ocorre porque uma cadeia de caracteres de consulta pode conter mais variáveis de cadeia de caracteres de consulta que o modelo correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-280">This is because a query string may contain more query string variables then the template it matches.</span></span>  
  
- <span data-ttu-id="e5ef2-281">?x=1</span><span class="sxs-lookup"><span data-stu-id="e5ef2-281">?x=1</span></span>  
  
- <span data-ttu-id="e5ef2-282">?x=1&y={var}</span><span class="sxs-lookup"><span data-stu-id="e5ef2-282">?x=1&y={var}</span></span>  
  
 <span data-ttu-id="e5ef2-283">"x = 1 & y = 3" corresponde a ambos os modelos.</span><span class="sxs-lookup"><span data-stu-id="e5ef2-283">"x=1&y=3" matches both templates.</span></span>  
  
- <span data-ttu-id="e5ef2-284">?x=3&y=4</span><span class="sxs-lookup"><span data-stu-id="e5ef2-284">?x=3&y=4</span></span>  
  
- <span data-ttu-id="e5ef2-285">?x=3&z=5</span><span class="sxs-lookup"><span data-stu-id="e5ef2-285">?x=3&z=5</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5ef2-286">Os caracteres á e á são considerados caracteres diferentes quando aparecem como parte de um caminho de URI ou <xref:System.UriTemplate> um literal de segmento de caminho (mas os caracteres a e a são considerados iguais).</span><span class="sxs-lookup"><span data-stu-id="e5ef2-286">The characters á and Á are considered to be different characters when they appear as part of a URI path or <xref:System.UriTemplate> path segment literal (but the characters a and A are considered to be the same).</span></span> <span data-ttu-id="e5ef2-287">Os caracteres á e á são considerados os mesmos caracteres quando aparecem como parte de um <xref:System.UriTemplate> {VariableName} ou uma cadeia de caracteres de consulta (e um e um também são considerados os mesmos caracteres).</span><span class="sxs-lookup"><span data-stu-id="e5ef2-287">The characters á and Á are considered to be the same characters when they appear as part of a <xref:System.UriTemplate> {variableName} or a query string (and a and A are also considered to be the same characters).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5ef2-288">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5ef2-288">See also</span></span>

- [<span data-ttu-id="e5ef2-289">Visão geral do modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="e5ef2-289">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="e5ef2-290">Modelo de objeto de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="e5ef2-290">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [<span data-ttu-id="e5ef2-291">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="e5ef2-291">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
- [<span data-ttu-id="e5ef2-292">Tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="e5ef2-292">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="e5ef2-293">Dispatcher de Tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="e5ef2-293">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
