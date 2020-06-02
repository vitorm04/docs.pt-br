---
title: Cadeias de Conexão
description: Saiba mais sobre cadeias de conexão em ADO.NET, que contêm informações de inicialização passadas como um parâmetro de um provedor de dados para uma fonte de dados.
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: baa6599a532746895cbb3920f2c623dd4c2be864
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287019"
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="7117e-103">Cadeias de caracteres de conexão no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7117e-103">Connection Strings in ADO.NET</span></span>

<span data-ttu-id="7117e-104">Uma cadeia de conexão contém informações de inicialização que são passadas como parâmetros de um provedor de dados para uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="7117e-104">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="7117e-105">O provedor de dados recebe a cadeia de conexão como o valor da <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="7117e-105">The data provider receives the connection string as the value of the <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="7117e-106">O provedor analisa a cadeia de conexão e garante que a sintaxe esteja correta e que as palavras-chave tenham suporte.</span><span class="sxs-lookup"><span data-stu-id="7117e-106">The provider parses the connection string and ensures that the syntax is correct and that the keywords are supported.</span></span> <span data-ttu-id="7117e-107">Em seguida, o <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> método passa os parâmetros de conexão analisados para a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="7117e-107">Then the <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> method passes the parsed connection parameters to the data source.</span></span> <span data-ttu-id="7117e-108">A fonte de dados executa uma validação adicional e estabelece uma conexão.</span><span class="sxs-lookup"><span data-stu-id="7117e-108">The data source performs further validation and establishes a connection.</span></span>

## <a name="connection-string-syntax"></a><span data-ttu-id="7117e-109">Sintaxe da cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="7117e-109">Connection string syntax</span></span>

<span data-ttu-id="7117e-110">Uma cadeia de conexão é uma lista delimitada por ponto-e-vírgula de pares de parâmetro de chave/valor:</span><span class="sxs-lookup"><span data-stu-id="7117e-110">A connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>

```csharp
keyword1=value; keyword2=value;
```

<span data-ttu-id="7117e-111">As palavras-chave não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="7117e-111">Keywords are not case-sensitive.</span></span> <span data-ttu-id="7117e-112">Os valores, no entanto, podem diferenciar maiúsculas de minúsculas, dependendo da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="7117e-112">Values, however, may be case-sensitive, depending on the data source.</span></span> <span data-ttu-id="7117e-113">As palavras-chave e os valores podem conter [caracteres de espaço em branco](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span><span class="sxs-lookup"><span data-stu-id="7117e-113">Both keywords and values may contain [whitespace characters](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span></span> <span data-ttu-id="7117e-114">Espaços em branco à esquerda e à direita são ignorados em palavras-chave e valores sem aspas.</span><span class="sxs-lookup"><span data-stu-id="7117e-114">Leading and trailing white space is ignored in keywords and unquoted values.</span></span>

<span data-ttu-id="7117e-115">Se um valor contiver ponto e vírgula, [caracteres de controle Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters)ou espaços em branco à esquerda ou à direita, ele deverá ser colocado entre aspas simples ou duplas.</span><span class="sxs-lookup"><span data-stu-id="7117e-115">If a value contains the semicolon, [Unicode control characters](https://en.wikipedia.org/wiki/Unicode_control_characters), or leading or trailing white space, it must be enclosed in single or double quotation marks.</span></span> <span data-ttu-id="7117e-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="7117e-116">For example:</span></span>

```csharp
Keyword=" whitespace  ";
Keyword='special;character';
```

<span data-ttu-id="7117e-117">O caractere delimitador pode não ocorrer dentro do valor que ele envolve.</span><span class="sxs-lookup"><span data-stu-id="7117e-117">The enclosing character may not occur within the value it encloses.</span></span> <span data-ttu-id="7117e-118">Portanto, um valor contendo aspas simples pode ser colocado entre aspas duplas, e vice-versa:</span><span class="sxs-lookup"><span data-stu-id="7117e-118">Therefore, a value containing single quotation marks can be enclosed only in double quotation marks, and vice versa:</span></span>

```csharp
Keyword='double"quotation;mark';
Keyword="single'quotation;mark";
```

<span data-ttu-id="7117e-119">Você também pode escapar do caractere delimitador usando dois juntos:</span><span class="sxs-lookup"><span data-stu-id="7117e-119">You can also escape the enclosing character by using two of them together:</span></span>

```csharp
Keyword="double""quotation";
Keyword='single''quotation';
```

<span data-ttu-id="7117e-120">As aspas em si, bem como o sinal de igual, não exigem saída, portanto, as seguintes cadeias de conexão são válidas:</span><span class="sxs-lookup"><span data-stu-id="7117e-120">The quotation marks themselves, as well as the equals sign, do not require escaping, so the following connection strings are valid:</span></span>

```csharp
Keyword=no "escaping" 'required';
Keyword=a=b=c
```

<span data-ttu-id="7117e-121">Como cada valor é lido até o próximo ponto e vírgula ou o final da cadeia de caracteres, o valor no último exemplo é `a=b=c` , e o ponto e vírgula final é opcional.</span><span class="sxs-lookup"><span data-stu-id="7117e-121">Since each value is read till the next semicolon or the end of string, the value in the latter example is `a=b=c`, and the final semicolon is optional.</span></span>

<span data-ttu-id="7117e-122">Todas as cadeias de conexão compartilham a mesma sintaxe básica descrita acima.</span><span class="sxs-lookup"><span data-stu-id="7117e-122">All connection strings share the same basic syntax described above.</span></span> <span data-ttu-id="7117e-123">O conjunto de palavras-chave reconhecidas depende do provedor, no entanto, e evoluiu ao longo dos anos de APIs anteriores, como *ODBC*.</span><span class="sxs-lookup"><span data-stu-id="7117e-123">The set of recognized keywords depends on the provider, however, and has evolved over the years from earlier APIs such as *ODBC*.</span></span> <span data-ttu-id="7117e-124">O provedor de dados de *.NET Framework* para *SQL Server* ( `SqlClient` ) dá suporte a muitas palavras-chave de APIs mais antigas, mas é geralmente mais flexível e aceita sinônimos para muitas das palavras-chave da cadeia de conexão comum.</span><span class="sxs-lookup"><span data-stu-id="7117e-124">The *.NET Framework* data provider for *SQL Server* (`SqlClient`) supports many keywords from older APIs, but is generally more flexible and accepts synonyms for many of the common connection string keywords.</span></span>

<span data-ttu-id="7117e-125">Digitar erros pode causar erros.</span><span class="sxs-lookup"><span data-stu-id="7117e-125">Typing mistakes can cause errors.</span></span> <span data-ttu-id="7117e-126">Por exemplo, `Integrated Security=true` é válido, mas `IntegratedSecurity=true` causa um erro.</span><span class="sxs-lookup"><span data-stu-id="7117e-126">For example, `Integrated Security=true` is valid, but `IntegratedSecurity=true` causes an error.</span></span>

<span data-ttu-id="7117e-127">Cadeias de conexão construídas manualmente em tempo de execução de entrada de usuário não validada são vulneráveis a ataques de injeção de cadeia de caracteres e ameaçam a segurança na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="7117e-127">Connection strings constructed manually at run time from unvalidated user input are vulnerable to string-injection attacks and jeopardize security at the data source.</span></span> <span data-ttu-id="7117e-128">Para resolver esses problemas, o *ADO.NET* 2,0 introduziu [construtores de cadeia de conexão](connection-string-builders.md) para cada provedor de dados de *.NET Framework* .</span><span class="sxs-lookup"><span data-stu-id="7117e-128">To address these problems, *ADO.NET* 2.0 introduced [connection string builders](connection-string-builders.md) for each *.NET Framework* data provider.</span></span> <span data-ttu-id="7117e-129">Esses construtores de cadeia de conexão expõem parâmetros como propriedades fortemente tipadas e possibilitam validar a cadeia de conexão antes que ela seja enviada para a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="7117e-129">These connection string builders expose parameters as strongly typed properties, and make it possible to validate the connection string before it's sent to the data source.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7117e-130">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="7117e-130">In This Section</span></span>

<span data-ttu-id="7117e-131">[Construtores de cadeia de conexão](connection-string-builders.md)</span><span class="sxs-lookup"><span data-stu-id="7117e-131">[Connection String Builders](connection-string-builders.md)</span></span>\
<span data-ttu-id="7117e-132">Demonstra como usar as classes `ConnectionStringBuilder` para construir cadeias de conexão válidas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7117e-132">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>

<span data-ttu-id="7117e-133">[Cadeias de conexão e arquivos de configuração](connection-strings-and-configuration-files.md)</span><span class="sxs-lookup"><span data-stu-id="7117e-133">[Connection Strings and Configuration Files](connection-strings-and-configuration-files.md)</span></span>\
<span data-ttu-id="7117e-134">Demonstra como armazenar e recuperar cadeias de conexão em arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="7117e-134">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>

<span data-ttu-id="7117e-135">[Sintaxe da cadeia de conexão](connection-string-syntax.md)</span><span class="sxs-lookup"><span data-stu-id="7117e-135">[Connection String Syntax](connection-string-syntax.md)</span></span>\
<span data-ttu-id="7117e-136">Descreve como configurar cadeias de conexão específicas do provedor para `SqlClient`, `OracleClient`, `OleDb` e `Odbc`.</span><span class="sxs-lookup"><span data-stu-id="7117e-136">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>

<span data-ttu-id="7117e-137">[Protegendo informações de conexão](protecting-connection-information.md)</span><span class="sxs-lookup"><span data-stu-id="7117e-137">[Protecting Connection Information](protecting-connection-information.md)</span></span>\
<span data-ttu-id="7117e-138">Demonstra técnicas para proteger informações usadas para se conectar a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="7117e-138">Demonstrates techniques for protecting information used to connect to a data source.</span></span>

## <a name="see-also"></a><span data-ttu-id="7117e-139">Veja também</span><span class="sxs-lookup"><span data-stu-id="7117e-139">See also</span></span>

- [<span data-ttu-id="7117e-140">Conectando a uma Fonte de Dados</span><span class="sxs-lookup"><span data-stu-id="7117e-140">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)
- [<span data-ttu-id="7117e-141">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7117e-141">ADO.NET Overview</span></span>](ado-net-overview.md)
