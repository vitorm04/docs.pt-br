---
title: SqlMetal.exe (ferramenta de geração de código)
ms.date: 03/30/2017
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
ms.openlocfilehash: d5b4c2b59b585b3d3a3584ef9055e70c9d998e85
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044087"
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="ee240-102">SqlMetal.exe (ferramenta de geração de código)</span><span class="sxs-lookup"><span data-stu-id="ee240-102">SqlMetal.exe (Code Generation Tool)</span></span>
<span data-ttu-id="ee240-103">A ferramenta de linha de comando SqlMetal gera o código e o mapeamento para o componente [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ee240-103">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the .NET Framework.</span></span> <span data-ttu-id="ee240-104">Aplicando-se opções exibidas mais à frente neste tópico, é possível instruir SqlMetal para executar diversas ações diferentes, dentre as quais estão:</span><span class="sxs-lookup"><span data-stu-id="ee240-104">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
- <span data-ttu-id="ee240-105">Em um banco de dados, gere atributos de código-fonte e mapeamento ou um arquivo de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="ee240-105">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
- <span data-ttu-id="ee240-106">Em um banco de dados, gera um arquivo .dbml (database markup language) intermediário para personalização.</span><span class="sxs-lookup"><span data-stu-id="ee240-106">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
- <span data-ttu-id="ee240-107">Em um arquivo .dbml, gere atributos de código e mapeamento ou um arquivo de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="ee240-107">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="ee240-108">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ee240-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="ee240-109">Por padrão, o arquivo está localizado em `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span><span class="sxs-lookup"><span data-stu-id="ee240-109">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="ee240-110">Se não instalar o Visual Studio, você também poderá obter o arquivo SQLMetal baixando o [SDK do Windows](https://go.microsoft.com/fwlink/?LinkId=142225).</span><span class="sxs-lookup"><span data-stu-id="ee240-110">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee240-111">Os desenvolvedores que usam o Visual Studio também podem usar o Object Relational Designer para gerar classes da entidade.</span><span class="sxs-lookup"><span data-stu-id="ee240-111">Developers who use Visual Studio can also use the Object Relational Designer to generate entity classes.</span></span> <span data-ttu-id="ee240-112">A abordagem de linha de comando é bem dimensionada para bancos de dados grandes.</span><span class="sxs-lookup"><span data-stu-id="ee240-112">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="ee240-113">Como SqlMetal é uma ferramenta de linha de comando, é possível usá-lo em um processo de compilação.</span><span class="sxs-lookup"><span data-stu-id="ee240-113">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="ee240-114">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor para Visual Studio (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="ee240-114">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="ee240-115">Para obter mais informações, consulte [Prompts de Comando](developer-command-prompt-for-vs.md). No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ee240-115">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee240-116">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ee240-116">Syntax</span></span>  
  
```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="ee240-117">Opções</span><span class="sxs-lookup"><span data-stu-id="ee240-117">Options</span></span>  
 <span data-ttu-id="ee240-118">Para exibir a lista de opções mais atual, digite `sqlmetal /?` em um prompt de comando no local instalado.</span><span class="sxs-lookup"><span data-stu-id="ee240-118">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="ee240-119">**Opções de Conexão**</span><span class="sxs-lookup"><span data-stu-id="ee240-119">**Connection Options**</span></span>  
  
|<span data-ttu-id="ee240-120">Opção</span><span class="sxs-lookup"><span data-stu-id="ee240-120">Option</span></span>|<span data-ttu-id="ee240-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee240-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ee240-122">**/server:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="ee240-122">**/server:** *\<name>*</span></span>|<span data-ttu-id="ee240-123">Especifica o nome do servidor do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ee240-123">Specifies database server name.</span></span>|  
|<span data-ttu-id="ee240-124">**/database:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="ee240-124">**/database:** *\<name>*</span></span>|<span data-ttu-id="ee240-125">Especifica o catálogo do banco de dados no servidor.</span><span class="sxs-lookup"><span data-stu-id="ee240-125">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="ee240-126">**/user:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="ee240-126">**/user:** *\<name>*</span></span>|<span data-ttu-id="ee240-127">Especifica a ID do usuário de logon. Valor padrão: usar a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="ee240-127">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="ee240-128">**/password:** *\<password>*</span><span class="sxs-lookup"><span data-stu-id="ee240-128">**/password:** *\<password>*</span></span>|<span data-ttu-id="ee240-129">Especifica a senha de logon.</span><span class="sxs-lookup"><span data-stu-id="ee240-129">Specifies logon password.</span></span> <span data-ttu-id="ee240-130">Valor padrão: usar a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="ee240-130">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="ee240-131">**/conn:** *\<connection string>*</span><span class="sxs-lookup"><span data-stu-id="ee240-131">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="ee240-132">Especifica a cadeia de conexão do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ee240-132">Specifies database connection string.</span></span> <span data-ttu-id="ee240-133">Não pode ser usada com as opções **/server**, **/database**, **/user** ou **/password**.</span><span class="sxs-lookup"><span data-stu-id="ee240-133">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="ee240-134">Não inclua o nome do arquivo na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="ee240-134">Do not include the file name in the connection string.</span></span> <span data-ttu-id="ee240-135">Em vez disso, adicione o nome do arquivo à linha de comando como o arquivo de entrada.</span><span class="sxs-lookup"><span data-stu-id="ee240-135">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="ee240-136">Por exemplo, a seguinte linha especifica “c:\northwnd.mdf” como o arquivo de entrada: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"** .</span><span class="sxs-lookup"><span data-stu-id="ee240-136">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="ee240-137">**/timeout:** *\<seconds>*</span><span class="sxs-lookup"><span data-stu-id="ee240-137">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="ee240-138">Especifica o valor de tempo limite em que SqlMetal acessa o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ee240-138">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="ee240-139">Valor padrão: 0 (ou seja, sem tempo limite).</span><span class="sxs-lookup"><span data-stu-id="ee240-139">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="ee240-140">**Opções de extração**</span><span class="sxs-lookup"><span data-stu-id="ee240-140">**Extraction options**</span></span>  
  
|<span data-ttu-id="ee240-141">Opção</span><span class="sxs-lookup"><span data-stu-id="ee240-141">Option</span></span>|<span data-ttu-id="ee240-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee240-142">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ee240-143">**/views**</span><span class="sxs-lookup"><span data-stu-id="ee240-143">**/views**</span></span>|<span data-ttu-id="ee240-144">Extrai exibições do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ee240-144">Extracts database views.</span></span>|  
|<span data-ttu-id="ee240-145">**/functions**</span><span class="sxs-lookup"><span data-stu-id="ee240-145">**/functions**</span></span>|<span data-ttu-id="ee240-146">Extrai funções do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ee240-146">Extracts database functions.</span></span>|  
|<span data-ttu-id="ee240-147">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="ee240-147">**/sprocs**</span></span>|<span data-ttu-id="ee240-148">Extrai procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="ee240-148">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="ee240-149">**Opções de saída**</span><span class="sxs-lookup"><span data-stu-id="ee240-149">**Output options**</span></span>  
  
|<span data-ttu-id="ee240-150">Opção</span><span class="sxs-lookup"><span data-stu-id="ee240-150">Option</span></span>|<span data-ttu-id="ee240-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee240-151">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ee240-152">**/dbml** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="ee240-152">**/dbml** *[:file]*</span></span>|<span data-ttu-id="ee240-153">Envia saídas como .dbml.</span><span class="sxs-lookup"><span data-stu-id="ee240-153">Sends output as .dbml.</span></span> <span data-ttu-id="ee240-154">Não pode ser usada com a opção **/map**.</span><span class="sxs-lookup"><span data-stu-id="ee240-154">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="ee240-155">**/code** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="ee240-155">**/code** *[:file]*</span></span>|<span data-ttu-id="ee240-156">Envia saídas como código-fonte.</span><span class="sxs-lookup"><span data-stu-id="ee240-156">Sends output as source code.</span></span> <span data-ttu-id="ee240-157">Não pode ser usada com a opção **/dbml**.</span><span class="sxs-lookup"><span data-stu-id="ee240-157">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="ee240-158">**/map** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="ee240-158">**/map** *[:file]*</span></span>|<span data-ttu-id="ee240-159">Gera um arquivo de mapeamento XML, em vez de atributos.</span><span class="sxs-lookup"><span data-stu-id="ee240-159">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="ee240-160">Não pode ser usada com a opção **/dbml**.</span><span class="sxs-lookup"><span data-stu-id="ee240-160">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="ee240-161">**Diversos**</span><span class="sxs-lookup"><span data-stu-id="ee240-161">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="ee240-162">Opção</span><span class="sxs-lookup"><span data-stu-id="ee240-162">Option</span></span>|<span data-ttu-id="ee240-163">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee240-163">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ee240-164">**/language:** *\<language>*</span><span class="sxs-lookup"><span data-stu-id="ee240-164">**/language:** *\<language>*</span></span>|<span data-ttu-id="ee240-165">Especifica a linguagem do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="ee240-165">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="ee240-166">Valid *\<language>* : vb, csharp.</span><span class="sxs-lookup"><span data-stu-id="ee240-166">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="ee240-167">Valor padrão: derivado da extensão de nome de arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="ee240-167">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="ee240-168">**/namespace:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="ee240-168">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="ee240-169">Especifica o namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="ee240-169">Specifies namespace of the generated code.</span></span> <span data-ttu-id="ee240-170">Valor padrão: sem namespace.</span><span class="sxs-lookup"><span data-stu-id="ee240-170">Default value: no namespace.</span></span>|  
|<span data-ttu-id="ee240-171">**/context:** *\<type>*</span><span class="sxs-lookup"><span data-stu-id="ee240-171">**/context:** *\<type>*</span></span>|<span data-ttu-id="ee240-172">Especifica o nome da classe de contexto dos dados.</span><span class="sxs-lookup"><span data-stu-id="ee240-172">Specifies name of data context class.</span></span> <span data-ttu-id="ee240-173">Valor padrão: derivado do nome do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ee240-173">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="ee240-174">**/entitybase:** *\<type>*</span><span class="sxs-lookup"><span data-stu-id="ee240-174">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="ee240-175">Especifica a classe base das classes de entidade no código gerado.</span><span class="sxs-lookup"><span data-stu-id="ee240-175">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="ee240-176">Valor padrão: as entidades não têm classe base.</span><span class="sxs-lookup"><span data-stu-id="ee240-176">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="ee240-177">**/pluralize**</span><span class="sxs-lookup"><span data-stu-id="ee240-177">**/pluralize**</span></span>|<span data-ttu-id="ee240-178">Pluraliza ou singulariza automaticamente nomes de classe e de membro.</span><span class="sxs-lookup"><span data-stu-id="ee240-178">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="ee240-179">Essa opção só está disponível na versão em inglês  dos EUA.</span><span class="sxs-lookup"><span data-stu-id="ee240-179">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="ee240-180">**/serialization:** *\<option>*</span><span class="sxs-lookup"><span data-stu-id="ee240-180">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="ee240-181">Gera classes serializáveis.</span><span class="sxs-lookup"><span data-stu-id="ee240-181">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="ee240-182">*\<opção>* válida: nenhum, unidirecional.</span><span class="sxs-lookup"><span data-stu-id="ee240-182">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="ee240-183">Valor padrão: nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ee240-183">Default value: None.</span></span><br /><br /> <span data-ttu-id="ee240-184">Para obter mais informações, consulte [Serialização](../data/adonet/sql/linq/serialization.md).</span><span class="sxs-lookup"><span data-stu-id="ee240-184">For more information, see [Serialization](../data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="ee240-185">**Arquivo de Entrada**</span><span class="sxs-lookup"><span data-stu-id="ee240-185">**Input File**</span></span>  
  
|<span data-ttu-id="ee240-186">Opção</span><span class="sxs-lookup"><span data-stu-id="ee240-186">Option</span></span>|<span data-ttu-id="ee240-187">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee240-187">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ee240-188">**\<input file>**</span><span class="sxs-lookup"><span data-stu-id="ee240-188">**\<input file>**</span></span>|<span data-ttu-id="ee240-189">Especifica um arquivo .mdf do SQL Server Express, um arquivo .sdf do SQL Server Compact 3.5 ou um arquivo intermediário .dbml.</span><span class="sxs-lookup"><span data-stu-id="ee240-189">Specifies a SQL Server Express .mdf file, a SQL Server Compact 3.5 .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee240-190">Comentários</span><span class="sxs-lookup"><span data-stu-id="ee240-190">Remarks</span></span>  
 <span data-ttu-id="ee240-191">A funcionalidade SqlMetal envolve, na realidade, duas etapas:</span><span class="sxs-lookup"><span data-stu-id="ee240-191">SqlMetal functionality actually involves two steps:</span></span>  
  
- <span data-ttu-id="ee240-192">Extraindo os metadados do banco de dados para um arquivo. dbml.</span><span class="sxs-lookup"><span data-stu-id="ee240-192">Extracting the metadata of the database into a .dbml file.</span></span>  
  
- <span data-ttu-id="ee240-193">Gerando um arquivo de saída do código.</span><span class="sxs-lookup"><span data-stu-id="ee240-193">Generating a code output file.</span></span>  
  
     <span data-ttu-id="ee240-194">Usando as opções da linha de comando apropriadas, é possível produzir o código-fonte do Visual Basic ou do C# ou produzir um arquivo de mapeamento de XML.</span><span class="sxs-lookup"><span data-stu-id="ee240-194">By using the appropriate command-line options, you can produce Visual Basic or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="ee240-195">Para extrair os metadados de um arquivo .mdf, você deve especificar o nome do arquivo .mdf depois de todas as outras opções.</span><span class="sxs-lookup"><span data-stu-id="ee240-195">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="ee240-196">Se nenhum **/server** for especificado, **localhost/sqlexpress** será suposto.</span><span class="sxs-lookup"><span data-stu-id="ee240-196">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 <span data-ttu-id="ee240-197">O Microsoft SQL Server 2005 acionará uma exceção se uma ou mais das seguintes condições forem verdadeiras:</span><span class="sxs-lookup"><span data-stu-id="ee240-197">Microsoft SQL Server 2005 throws an exception if one or more of the following conditions are true:</span></span>  
  
- <span data-ttu-id="ee240-198">SqlMetal tenta extrair um procedimento armazenado que se chama.</span><span class="sxs-lookup"><span data-stu-id="ee240-198">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
- <span data-ttu-id="ee240-199">O nível de aninhamento de um procedimento armazenado, função ou uma exibição excede 32.</span><span class="sxs-lookup"><span data-stu-id="ee240-199">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="ee240-200">SqlMetal captura essa exceção e a relata como um aviso.</span><span class="sxs-lookup"><span data-stu-id="ee240-200">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="ee240-201">Para especificar um nome do arquivo de entrada, adicione o nome do arquivo à linha de comando como o arquivo de entrada.</span><span class="sxs-lookup"><span data-stu-id="ee240-201">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="ee240-202">Não há suporte para a inclusão do nome de arquivo na cadeia de conexão (usando a opção **/conn**).</span><span class="sxs-lookup"><span data-stu-id="ee240-202">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ee240-203">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ee240-203">Examples</span></span>  
 <span data-ttu-id="ee240-204">Gera um arquivo. dbml que inclui metadados SQL extraídos:</span><span class="sxs-lookup"><span data-stu-id="ee240-204">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="ee240-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span><span class="sxs-lookup"><span data-stu-id="ee240-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="ee240-206">Gera um arquivo. dbml que inclui metadados SQL extraídos de um arquivo .mdf usando-se o SQL Server Express:</span><span class="sxs-lookup"><span data-stu-id="ee240-206">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="ee240-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span><span class="sxs-lookup"><span data-stu-id="ee240-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="ee240-208">Gera um arquivo. dbml que inclui metadados SQL extraídos do SQL Server Express:</span><span class="sxs-lookup"><span data-stu-id="ee240-208">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="ee240-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="ee240-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="ee240-210">Gera o código-fonte com base em um arquivo de metadados .dbml:</span><span class="sxs-lookup"><span data-stu-id="ee240-210">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="ee240-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span><span class="sxs-lookup"><span data-stu-id="ee240-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="ee240-212">Gera o código-fonte com base nos metadados SQL diretamente:</span><span class="sxs-lookup"><span data-stu-id="ee240-212">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="ee240-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span><span class="sxs-lookup"><span data-stu-id="ee240-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee240-214">Ao usar a opção **/pluralize** com o banco de dados de exemplo Northwind, observe o comportamento a seguir.</span><span class="sxs-lookup"><span data-stu-id="ee240-214">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="ee240-215">Quando SqlMetal cria nomes de tipo de linha para tabelas, os nomes de tabela são singulares.</span><span class="sxs-lookup"><span data-stu-id="ee240-215">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="ee240-216">Quando ele cria propriedades <xref:System.Data.Linq.DataContext> para tabelas, os nomes de tabela serão plurais.</span><span class="sxs-lookup"><span data-stu-id="ee240-216">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="ee240-217">Coincidentemente, as tabelas no banco de dados de exemplo Northwind já são plurais.</span><span class="sxs-lookup"><span data-stu-id="ee240-217">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="ee240-218">Por isso, você não vê essa parte funcionando.</span><span class="sxs-lookup"><span data-stu-id="ee240-218">Therefore, you do not see that part working.</span></span> <span data-ttu-id="ee240-219">Embora seja uma prática comum nomear tabelas de banco de dados singulares, também é uma prática comum no .NET nomear as coleções plurais.</span><span class="sxs-lookup"><span data-stu-id="ee240-219">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee240-220">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee240-220">See also</span></span>

- [<span data-ttu-id="ee240-221">Como: gerar o modelo de objeto em Visual Basic ou em C#</span><span class="sxs-lookup"><span data-stu-id="ee240-221">How to: Generate the Object Model in Visual Basic or C#</span></span>](../data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [<span data-ttu-id="ee240-222">Geração de código em LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ee240-222">Code Generation in LINQ to SQL</span></span>](../data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="ee240-223">Mapeamento Externo</span><span class="sxs-lookup"><span data-stu-id="ee240-223">External Mapping</span></span>](../data/adonet/sql/linq/external-mapping.md)
