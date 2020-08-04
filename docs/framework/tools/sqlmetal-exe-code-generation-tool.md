---
title: SqlMetal.exe (ferramenta de geração de código)
description: Entenda SqlMetal.exe, a ferramenta de geração de código. Use a ferramenta para gerar código e mapeamento para o componente LINQ to SQL do .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
ms.openlocfilehash: 84cad85a7a9fc4b420b57543b7f258607be4ab52
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517042"
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="b851c-104">SqlMetal.exe (ferramenta de geração de código)</span><span class="sxs-lookup"><span data-stu-id="b851c-104">SqlMetal.exe (Code Generation Tool)</span></span>
<span data-ttu-id="b851c-105">A ferramenta de linha de comando SqlMetal gera o código e o mapeamento para o componente [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b851c-105">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the .NET Framework.</span></span> <span data-ttu-id="b851c-106">Aplicando-se opções exibidas mais à frente neste tópico, é possível instruir SqlMetal para executar diversas ações diferentes, dentre as quais estão:</span><span class="sxs-lookup"><span data-stu-id="b851c-106">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
- <span data-ttu-id="b851c-107">Em um banco de dados, gere atributos de código-fonte e mapeamento ou um arquivo de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="b851c-107">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
- <span data-ttu-id="b851c-108">Em um banco de dados, gera um arquivo .dbml (database markup language) intermediário para personalização.</span><span class="sxs-lookup"><span data-stu-id="b851c-108">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
- <span data-ttu-id="b851c-109">Em um arquivo .dbml, gere atributos de código e mapeamento ou um arquivo de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="b851c-109">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="b851c-110">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b851c-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="b851c-111">Por padrão, o arquivo está localizado em `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span><span class="sxs-lookup"><span data-stu-id="b851c-111">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="b851c-112">Se não instalar o Visual Studio, você também poderá obter o arquivo SQLMetal baixando o [SDK do Windows](https://go.microsoft.com/fwlink/?LinkId=142225).</span><span class="sxs-lookup"><span data-stu-id="b851c-112">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b851c-113">Os desenvolvedores que usam o Visual Studio também podem usar o Object Relational Designer para gerar classes da entidade.</span><span class="sxs-lookup"><span data-stu-id="b851c-113">Developers who use Visual Studio can also use the Object Relational Designer to generate entity classes.</span></span> <span data-ttu-id="b851c-114">A abordagem de linha de comando é bem dimensionada para bancos de dados grandes.</span><span class="sxs-lookup"><span data-stu-id="b851c-114">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="b851c-115">Como SqlMetal é uma ferramenta de linha de comando, é possível usá-lo em um processo de compilação.</span><span class="sxs-lookup"><span data-stu-id="b851c-115">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="b851c-116">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor para Visual Studio (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="b851c-116">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="b851c-117">Para obter mais informações, consulte [Prompts de Comando](developer-command-prompt-for-vs.md). No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b851c-117">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b851c-118">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b851c-118">Syntax</span></span>  
  
```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="b851c-119">Opções</span><span class="sxs-lookup"><span data-stu-id="b851c-119">Options</span></span>  
 <span data-ttu-id="b851c-120">Para exibir a lista de opções mais atual, digite `sqlmetal /?` em um prompt de comando no local instalado.</span><span class="sxs-lookup"><span data-stu-id="b851c-120">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="b851c-121">**Opções de conexão**</span><span class="sxs-lookup"><span data-stu-id="b851c-121">**Connection Options**</span></span>  
  
|<span data-ttu-id="b851c-122">Opção</span><span class="sxs-lookup"><span data-stu-id="b851c-122">Option</span></span>|<span data-ttu-id="b851c-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="b851c-123">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b851c-124">\**/Server:\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="b851c-124">**/server:** *\<name>*</span></span>|<span data-ttu-id="b851c-125">Especifica o nome do servidor do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b851c-125">Specifies database server name.</span></span>|  
|<span data-ttu-id="b851c-126">\**/Database:\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="b851c-126">**/database:** *\<name>*</span></span>|<span data-ttu-id="b851c-127">Especifica o catálogo do banco de dados no servidor.</span><span class="sxs-lookup"><span data-stu-id="b851c-127">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="b851c-128">\**/User:\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="b851c-128">**/user:** *\<name>*</span></span>|<span data-ttu-id="b851c-129">Especifica a ID de usuário de logon. Valor padrão: Use a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="b851c-129">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="b851c-130">\**/password:\*\*\*\<password>*</span><span class="sxs-lookup"><span data-stu-id="b851c-130">**/password:** *\<password>*</span></span>|<span data-ttu-id="b851c-131">Especifica a senha de logon.</span><span class="sxs-lookup"><span data-stu-id="b851c-131">Specifies logon password.</span></span> <span data-ttu-id="b851c-132">Valor padrão: Usar autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="b851c-132">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="b851c-133">\**/Conn:\*\*\*\<connection string>*</span><span class="sxs-lookup"><span data-stu-id="b851c-133">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="b851c-134">Especifica a cadeia de conexão do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b851c-134">Specifies database connection string.</span></span> <span data-ttu-id="b851c-135">Não pode ser usada com as opções **/server**, **/database**, **/user** ou **/password**.</span><span class="sxs-lookup"><span data-stu-id="b851c-135">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="b851c-136">Não inclua o nome do arquivo na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="b851c-136">Do not include the file name in the connection string.</span></span> <span data-ttu-id="b851c-137">Em vez disso, adicione o nome do arquivo à linha de comando como o arquivo de entrada.</span><span class="sxs-lookup"><span data-stu-id="b851c-137">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="b851c-138">Por exemplo, a seguinte linha especifica “c:\northwnd.mdf” como o arquivo de entrada: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span><span class="sxs-lookup"><span data-stu-id="b851c-138">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="b851c-139">\**/timeout:\*\*\*\<seconds>*</span><span class="sxs-lookup"><span data-stu-id="b851c-139">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="b851c-140">Especifica o valor de tempo limite em que SqlMetal acessa o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b851c-140">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="b851c-141">Valor padrão: 0 (ou seja, sem tempo limite).</span><span class="sxs-lookup"><span data-stu-id="b851c-141">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="b851c-142">**Opções de extração**</span><span class="sxs-lookup"><span data-stu-id="b851c-142">**Extraction options**</span></span>  
  
|<span data-ttu-id="b851c-143">Opção</span><span class="sxs-lookup"><span data-stu-id="b851c-143">Option</span></span>|<span data-ttu-id="b851c-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="b851c-144">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b851c-145">**/views**</span><span class="sxs-lookup"><span data-stu-id="b851c-145">**/views**</span></span>|<span data-ttu-id="b851c-146">Extrai exibições do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b851c-146">Extracts database views.</span></span>|  
|<span data-ttu-id="b851c-147">**/functions**</span><span class="sxs-lookup"><span data-stu-id="b851c-147">**/functions**</span></span>|<span data-ttu-id="b851c-148">Extrai funções do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b851c-148">Extracts database functions.</span></span>|  
|<span data-ttu-id="b851c-149">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="b851c-149">**/sprocs**</span></span>|<span data-ttu-id="b851c-150">Extrai procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="b851c-150">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="b851c-151">**Opções de saída**</span><span class="sxs-lookup"><span data-stu-id="b851c-151">**Output options**</span></span>  
  
|<span data-ttu-id="b851c-152">Opção</span><span class="sxs-lookup"><span data-stu-id="b851c-152">Option</span></span>|<span data-ttu-id="b851c-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="b851c-153">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b851c-154">**/dbml** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="b851c-154">**/dbml** *[:file]*</span></span>|<span data-ttu-id="b851c-155">Envia saídas como .dbml.</span><span class="sxs-lookup"><span data-stu-id="b851c-155">Sends output as .dbml.</span></span> <span data-ttu-id="b851c-156">Não pode ser usada com a opção **/map**.</span><span class="sxs-lookup"><span data-stu-id="b851c-156">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="b851c-157">**/code** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="b851c-157">**/code** *[:file]*</span></span>|<span data-ttu-id="b851c-158">Envia saídas como código-fonte.</span><span class="sxs-lookup"><span data-stu-id="b851c-158">Sends output as source code.</span></span> <span data-ttu-id="b851c-159">Não pode ser usada com a opção **/dbml**.</span><span class="sxs-lookup"><span data-stu-id="b851c-159">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="b851c-160">**/map** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="b851c-160">**/map** *[:file]*</span></span>|<span data-ttu-id="b851c-161">Gera um arquivo de mapeamento XML, em vez de atributos.</span><span class="sxs-lookup"><span data-stu-id="b851c-161">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="b851c-162">Não pode ser usada com a opção **/dbml**.</span><span class="sxs-lookup"><span data-stu-id="b851c-162">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="b851c-163">**Diversos**</span><span class="sxs-lookup"><span data-stu-id="b851c-163">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="b851c-164">Opção</span><span class="sxs-lookup"><span data-stu-id="b851c-164">Option</span></span>|<span data-ttu-id="b851c-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="b851c-165">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b851c-166">\**/Language:\*\*\*\<language>*</span><span class="sxs-lookup"><span data-stu-id="b851c-166">**/language:** *\<language>*</span></span>|<span data-ttu-id="b851c-167">Especifica a linguagem do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="b851c-167">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="b851c-168">Válido *\<language>* : VB, Csharp.</span><span class="sxs-lookup"><span data-stu-id="b851c-168">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="b851c-169">Valor padrão: Derivado da extensão no nome de arquivo do código.</span><span class="sxs-lookup"><span data-stu-id="b851c-169">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="b851c-170">\**/namespace:\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="b851c-170">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="b851c-171">Especifica o namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="b851c-171">Specifies namespace of the generated code.</span></span> <span data-ttu-id="b851c-172">Valor padrão: sem namespace.</span><span class="sxs-lookup"><span data-stu-id="b851c-172">Default value: no namespace.</span></span>|  
|<span data-ttu-id="b851c-173">\**/Context:\*\*\*\<type>*</span><span class="sxs-lookup"><span data-stu-id="b851c-173">**/context:** *\<type>*</span></span>|<span data-ttu-id="b851c-174">Especifica o nome da classe de contexto dos dados.</span><span class="sxs-lookup"><span data-stu-id="b851c-174">Specifies name of data context class.</span></span> <span data-ttu-id="b851c-175">Valor padrão: Derivado do nome do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b851c-175">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="b851c-176">\**/EntityBase:\*\*\*\<type>*</span><span class="sxs-lookup"><span data-stu-id="b851c-176">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="b851c-177">Especifica a classe base das classes de entidade no código gerado.</span><span class="sxs-lookup"><span data-stu-id="b851c-177">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="b851c-178">Valor padrão: Entidades não têm classe base.</span><span class="sxs-lookup"><span data-stu-id="b851c-178">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="b851c-179">**/pluralize**</span><span class="sxs-lookup"><span data-stu-id="b851c-179">**/pluralize**</span></span>|<span data-ttu-id="b851c-180">Pluraliza ou singulariza automaticamente nomes de classe e de membro.</span><span class="sxs-lookup"><span data-stu-id="b851c-180">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="b851c-181">Essa opção só está disponível na versão em inglês dos EUA.</span><span class="sxs-lookup"><span data-stu-id="b851c-181">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="b851c-182">\**/Serialization:\*\*\*\<option>*</span><span class="sxs-lookup"><span data-stu-id="b851c-182">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="b851c-183">Gera classes serializáveis.</span><span class="sxs-lookup"><span data-stu-id="b851c-183">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="b851c-184">Válido *\<option>* : nenhum, unidirecional.</span><span class="sxs-lookup"><span data-stu-id="b851c-184">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="b851c-185">Valor padrão: Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b851c-185">Default value: None.</span></span><br /><br /> <span data-ttu-id="b851c-186">Para obter mais informações, consulte [Serialização](../data/adonet/sql/linq/serialization.md).</span><span class="sxs-lookup"><span data-stu-id="b851c-186">For more information, see [Serialization](../data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="b851c-187">**Arquivo de entrada**</span><span class="sxs-lookup"><span data-stu-id="b851c-187">**Input File**</span></span>  
  
|<span data-ttu-id="b851c-188">Opção</span><span class="sxs-lookup"><span data-stu-id="b851c-188">Option</span></span>|<span data-ttu-id="b851c-189">Descrição</span><span class="sxs-lookup"><span data-stu-id="b851c-189">Description</span></span>|  
|------------|-----------------|  
|**\<input file>**|<span data-ttu-id="b851c-190">Especifica um arquivo .mdf do SQL Server Express, um arquivo .sdf do SQL Server Compact 3.5 ou um arquivo intermediário .dbml.</span><span class="sxs-lookup"><span data-stu-id="b851c-190">Specifies a SQL Server Express .mdf file, a SQL Server Compact 3.5 .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b851c-191">Comentários</span><span class="sxs-lookup"><span data-stu-id="b851c-191">Remarks</span></span>  
 <span data-ttu-id="b851c-192">A funcionalidade SqlMetal envolve, na realidade, duas etapas:</span><span class="sxs-lookup"><span data-stu-id="b851c-192">SqlMetal functionality actually involves two steps:</span></span>  
  
- <span data-ttu-id="b851c-193">Extraindo os metadados do banco de dados para um arquivo. dbml.</span><span class="sxs-lookup"><span data-stu-id="b851c-193">Extracting the metadata of the database into a .dbml file.</span></span>  
  
- <span data-ttu-id="b851c-194">Gerando um arquivo de saída do código.</span><span class="sxs-lookup"><span data-stu-id="b851c-194">Generating a code output file.</span></span>  
  
     <span data-ttu-id="b851c-195">Usando as opções da linha de comando apropriadas, é possível produzir o código-fonte do Visual Basic ou do C# ou produzir um arquivo de mapeamento de XML.</span><span class="sxs-lookup"><span data-stu-id="b851c-195">By using the appropriate command-line options, you can produce Visual Basic or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="b851c-196">Para extrair os metadados de um arquivo .mdf, você deve especificar o nome do arquivo .mdf depois de todas as outras opções.</span><span class="sxs-lookup"><span data-stu-id="b851c-196">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="b851c-197">Se nenhum **/server** for especificado, **localhost/sqlexpress** será suposto.</span><span class="sxs-lookup"><span data-stu-id="b851c-197">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 <span data-ttu-id="b851c-198">O Microsoft SQL Server 2005 acionará uma exceção se uma ou mais das seguintes condições forem verdadeiras:</span><span class="sxs-lookup"><span data-stu-id="b851c-198">Microsoft SQL Server 2005 throws an exception if one or more of the following conditions are true:</span></span>  
  
- <span data-ttu-id="b851c-199">SqlMetal tenta extrair um procedimento armazenado que se chama.</span><span class="sxs-lookup"><span data-stu-id="b851c-199">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
- <span data-ttu-id="b851c-200">O nível de aninhamento de um procedimento armazenado, função ou uma exibição excede 32.</span><span class="sxs-lookup"><span data-stu-id="b851c-200">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="b851c-201">SqlMetal captura essa exceção e a relata como um aviso.</span><span class="sxs-lookup"><span data-stu-id="b851c-201">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="b851c-202">Para especificar um nome do arquivo de entrada, adicione o nome do arquivo à linha de comando como o arquivo de entrada.</span><span class="sxs-lookup"><span data-stu-id="b851c-202">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="b851c-203">Não há suporte para a inclusão do nome de arquivo na cadeia de conexão (usando a opção **/conn**).</span><span class="sxs-lookup"><span data-stu-id="b851c-203">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b851c-204">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b851c-204">Examples</span></span>  
 <span data-ttu-id="b851c-205">Gera um arquivo. dbml que inclui metadados SQL extraídos:</span><span class="sxs-lookup"><span data-stu-id="b851c-205">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="b851c-206">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span><span class="sxs-lookup"><span data-stu-id="b851c-206">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="b851c-207">Gera um arquivo. dbml que inclui metadados SQL extraídos de um arquivo .mdf usando-se o SQL Server Express:</span><span class="sxs-lookup"><span data-stu-id="b851c-207">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="b851c-208">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span><span class="sxs-lookup"><span data-stu-id="b851c-208">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="b851c-209">Gera um arquivo. dbml que inclui metadados SQL extraídos do SQL Server Express:</span><span class="sxs-lookup"><span data-stu-id="b851c-209">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="b851c-210">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="b851c-210">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="b851c-211">Gera o código-fonte com base em um arquivo de metadados .dbml:</span><span class="sxs-lookup"><span data-stu-id="b851c-211">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="b851c-212">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span><span class="sxs-lookup"><span data-stu-id="b851c-212">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="b851c-213">Gera o código-fonte com base nos metadados SQL diretamente:</span><span class="sxs-lookup"><span data-stu-id="b851c-213">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="b851c-214">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span><span class="sxs-lookup"><span data-stu-id="b851c-214">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b851c-215">Ao usar a opção **/pluralize** com o banco de dados de exemplo Northwind, observe o comportamento a seguir.</span><span class="sxs-lookup"><span data-stu-id="b851c-215">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="b851c-216">Quando SqlMetal cria nomes de tipo de linha para tabelas, os nomes de tabela são singulares.</span><span class="sxs-lookup"><span data-stu-id="b851c-216">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="b851c-217">Quando ele cria propriedades <xref:System.Data.Linq.DataContext> para tabelas, os nomes de tabela serão plurais.</span><span class="sxs-lookup"><span data-stu-id="b851c-217">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="b851c-218">Coincidentemente, as tabelas no banco de dados de exemplo Northwind já são plurais.</span><span class="sxs-lookup"><span data-stu-id="b851c-218">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="b851c-219">Por isso, você não vê essa parte funcionando.</span><span class="sxs-lookup"><span data-stu-id="b851c-219">Therefore, you do not see that part working.</span></span> <span data-ttu-id="b851c-220">Embora seja uma prática comum nomear tabelas de banco de dados singulares, também é uma prática comum no .NET nomear as coleções plurais.</span><span class="sxs-lookup"><span data-stu-id="b851c-220">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b851c-221">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b851c-221">See also</span></span>

- [<span data-ttu-id="b851c-222">Como: gerar o modelo de objeto em Visual Basic ou em C#</span><span class="sxs-lookup"><span data-stu-id="b851c-222">How to: Generate the Object Model in Visual Basic or C#</span></span>](../data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [<span data-ttu-id="b851c-223">Geração de código em LINQ para SQL</span><span class="sxs-lookup"><span data-stu-id="b851c-223">Code Generation in LINQ to SQL</span></span>](../data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="b851c-224">Mapeamento externo</span><span class="sxs-lookup"><span data-stu-id="b851c-224">External Mapping</span></span>](../data/adonet/sql/linq/external-mapping.md)
