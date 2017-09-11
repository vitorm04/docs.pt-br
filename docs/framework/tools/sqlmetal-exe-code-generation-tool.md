---
title: "SqlMetal.exe (ferramenta de geração de código)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
caps.latest.revision: 43
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6d0ac9c682c60db8eb9e5188a71916dc5d97de60
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="518aa-102">SqlMetal.exe (ferramenta de geração de código)</span><span class="sxs-lookup"><span data-stu-id="518aa-102">SqlMetal.exe (Code Generation Tool)</span></span>
<span data-ttu-id="518aa-103">A ferramenta de linha de comando SqlMetal gera o código e o mapeamento para o componente [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] do [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="518aa-103">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="518aa-104">Aplicando-se opções exibidas mais à frente neste tópico, é possível instruir SqlMetal para executar diversas ações diferentes, dentre as quais estão:</span><span class="sxs-lookup"><span data-stu-id="518aa-104">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
-   <span data-ttu-id="518aa-105">Em um banco de dados, gere atributos de código-fonte e mapeamento ou um arquivo de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="518aa-105">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
-   <span data-ttu-id="518aa-106">Em um banco de dados, gera um arquivo .dbml (database markup language) intermediário para personalização.</span><span class="sxs-lookup"><span data-stu-id="518aa-106">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
-   <span data-ttu-id="518aa-107">Em um arquivo .dbml, gere atributos de código e mapeamento ou um arquivo de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="518aa-107">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="518aa-108">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="518aa-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="518aa-109">Por padrão, o arquivo está localizado em `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span><span class="sxs-lookup"><span data-stu-id="518aa-109">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="518aa-110">Se não instalar o Visual Studio, você também poderá obter o arquivo SQLMetal baixando o [SDK do Windows](http://go.microsoft.com/fwlink/?LinkId=142225).</span><span class="sxs-lookup"><span data-stu-id="518aa-110">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="518aa-111">Os desenvolvedores que usam o Visual Studio também podem usar [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] para gerar classes da entidade.</span><span class="sxs-lookup"><span data-stu-id="518aa-111">Developers who use Visual Studio can also use the [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] to generate entity classes.</span></span> <span data-ttu-id="518aa-112">A abordagem de linha de comando é bem dimensionada para bancos de dados grandes.</span><span class="sxs-lookup"><span data-stu-id="518aa-112">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="518aa-113">Como SqlMetal é uma ferramenta de linha de comando, é possível usá-lo em um processo de compilação.</span><span class="sxs-lookup"><span data-stu-id="518aa-113">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="518aa-114">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="518aa-114">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="518aa-115">Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md). No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="518aa-115">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="518aa-116">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="518aa-116">Syntax</span></span>  
  
```  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="518aa-117">Opções</span><span class="sxs-lookup"><span data-stu-id="518aa-117">Options</span></span>  
 <span data-ttu-id="518aa-118">Para exibir a lista de opções mais atual, digite `sqlmetal /?` em um prompt de comando no local instalado.</span><span class="sxs-lookup"><span data-stu-id="518aa-118">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="518aa-119">**Opções de Conexão**</span><span class="sxs-lookup"><span data-stu-id="518aa-119">**Connection Options**</span></span>  
  
|<span data-ttu-id="518aa-120">Opção</span><span class="sxs-lookup"><span data-stu-id="518aa-120">Option</span></span>|<span data-ttu-id="518aa-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="518aa-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="518aa-122">**/server:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="518aa-122">**/server:** *\<name>*</span></span>|<span data-ttu-id="518aa-123">Especifica o nome do servidor do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="518aa-123">Specifies database server name.</span></span>|  
|<span data-ttu-id="518aa-124">**/database:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="518aa-124">**/database:** *\<name>*</span></span>|<span data-ttu-id="518aa-125">Especifica o catálogo do banco de dados no servidor.</span><span class="sxs-lookup"><span data-stu-id="518aa-125">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="518aa-126">**/user:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="518aa-126">**/user:** *\<name>*</span></span>|<span data-ttu-id="518aa-127">Especifica a ID do usuário de logon.</span><span class="sxs-lookup"><span data-stu-id="518aa-127">Specifies logon user id.</span></span> <span data-ttu-id="518aa-128">Valor padrão: Usar autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="518aa-128">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="518aa-129">**/password:** *\<password>*</span><span class="sxs-lookup"><span data-stu-id="518aa-129">**/password:** *\<password>*</span></span>|<span data-ttu-id="518aa-130">Especifica a senha de logon.</span><span class="sxs-lookup"><span data-stu-id="518aa-130">Specifies logon password.</span></span> <span data-ttu-id="518aa-131">Valor padrão: Usar autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="518aa-131">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="518aa-132">**/conn:** *\<connection string>*</span><span class="sxs-lookup"><span data-stu-id="518aa-132">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="518aa-133">Especifica a cadeia de conexão do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="518aa-133">Specifies database connection string.</span></span> <span data-ttu-id="518aa-134">Não pode ser usada com as opções **/server**, **/database**, **/user** ou **/password**.</span><span class="sxs-lookup"><span data-stu-id="518aa-134">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="518aa-135">Não inclua o nome do arquivo na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="518aa-135">Do not include the file name in the connection string.</span></span> <span data-ttu-id="518aa-136">Em vez disso, adicione o nome do arquivo à linha de comando como o arquivo de entrada.</span><span class="sxs-lookup"><span data-stu-id="518aa-136">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="518aa-137">Por exemplo, a seguinte linha especifica “c:\northwnd.mdf” como o arquivo de entrada: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span><span class="sxs-lookup"><span data-stu-id="518aa-137">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="518aa-138">**/timeout:** *\<seconds>*</span><span class="sxs-lookup"><span data-stu-id="518aa-138">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="518aa-139">Especifica o valor de tempo limite em que SqlMetal acessa o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="518aa-139">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="518aa-140">Valor padrão: 0 (ou seja, sem tempo limite).</span><span class="sxs-lookup"><span data-stu-id="518aa-140">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="518aa-141">**Opções de extração**</span><span class="sxs-lookup"><span data-stu-id="518aa-141">**Extraction options**</span></span>  
  
|<span data-ttu-id="518aa-142">Opção</span><span class="sxs-lookup"><span data-stu-id="518aa-142">Option</span></span>|<span data-ttu-id="518aa-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="518aa-143">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="518aa-144">**/views**</span><span class="sxs-lookup"><span data-stu-id="518aa-144">**/views**</span></span>|<span data-ttu-id="518aa-145">Extrai exibições do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="518aa-145">Extracts database views.</span></span>|  
|<span data-ttu-id="518aa-146">**/functions**</span><span class="sxs-lookup"><span data-stu-id="518aa-146">**/functions**</span></span>|<span data-ttu-id="518aa-147">Extrai funções do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="518aa-147">Extracts database functions.</span></span>|  
|<span data-ttu-id="518aa-148">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="518aa-148">**/sprocs**</span></span>|<span data-ttu-id="518aa-149">Extrai procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="518aa-149">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="518aa-150">**Opções de saída**</span><span class="sxs-lookup"><span data-stu-id="518aa-150">**Output options**</span></span>  
  
|<span data-ttu-id="518aa-151">Opção</span><span class="sxs-lookup"><span data-stu-id="518aa-151">Option</span></span>|<span data-ttu-id="518aa-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="518aa-152">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="518aa-153">**/dbml** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="518aa-153">**/dbml** *[:file]*</span></span>|<span data-ttu-id="518aa-154">Envia saídas como .dbml.</span><span class="sxs-lookup"><span data-stu-id="518aa-154">Sends output as .dbml.</span></span> <span data-ttu-id="518aa-155">Não pode ser usada com a opção **/map**.</span><span class="sxs-lookup"><span data-stu-id="518aa-155">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="518aa-156">**/code** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="518aa-156">**/code** *[:file]*</span></span>|<span data-ttu-id="518aa-157">Envia saídas como código-fonte.</span><span class="sxs-lookup"><span data-stu-id="518aa-157">Sends output as source code.</span></span> <span data-ttu-id="518aa-158">Não pode ser usada com a opção **/dbml**.</span><span class="sxs-lookup"><span data-stu-id="518aa-158">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="518aa-159">**/map** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="518aa-159">**/map** *[:file]*</span></span>|<span data-ttu-id="518aa-160">Gera um arquivo de mapeamento XML, em vez de atributos.</span><span class="sxs-lookup"><span data-stu-id="518aa-160">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="518aa-161">Não pode ser usada com a opção **/dbml**.</span><span class="sxs-lookup"><span data-stu-id="518aa-161">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="518aa-162">**Diversos**</span><span class="sxs-lookup"><span data-stu-id="518aa-162">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="518aa-163">Opção</span><span class="sxs-lookup"><span data-stu-id="518aa-163">Option</span></span>|<span data-ttu-id="518aa-164">Descrição</span><span class="sxs-lookup"><span data-stu-id="518aa-164">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="518aa-165">**/language:** *\<language>*</span><span class="sxs-lookup"><span data-stu-id="518aa-165">**/language:** *\<language>*</span></span>|<span data-ttu-id="518aa-166">Especifica a linguagem do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="518aa-166">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="518aa-167">Valid *\<language>*: vb, csharp.</span><span class="sxs-lookup"><span data-stu-id="518aa-167">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="518aa-168">Valor padrão: Derivado da extensão no nome de arquivo do código.</span><span class="sxs-lookup"><span data-stu-id="518aa-168">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="518aa-169">**/namespace:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="518aa-169">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="518aa-170">Especifica o namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="518aa-170">Specifies namespace of the generated code.</span></span> <span data-ttu-id="518aa-171">Valor padrão: sem namespace.</span><span class="sxs-lookup"><span data-stu-id="518aa-171">Default value: no namespace.</span></span>|  
|<span data-ttu-id="518aa-172">**/context:** *\<type>*</span><span class="sxs-lookup"><span data-stu-id="518aa-172">**/context:** *\<type>*</span></span>|<span data-ttu-id="518aa-173">Especifica o nome da classe de contexto dos dados.</span><span class="sxs-lookup"><span data-stu-id="518aa-173">Specifies name of data context class.</span></span> <span data-ttu-id="518aa-174">Valor padrão: Derivado do nome do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="518aa-174">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="518aa-175">**/entitybase:** *\<type>*</span><span class="sxs-lookup"><span data-stu-id="518aa-175">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="518aa-176">Especifica a classe base das classes de entidade no código gerado.</span><span class="sxs-lookup"><span data-stu-id="518aa-176">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="518aa-177">Valor padrão: Entidades não têm classe base.</span><span class="sxs-lookup"><span data-stu-id="518aa-177">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="518aa-178">**/pluralize**</span><span class="sxs-lookup"><span data-stu-id="518aa-178">**/pluralize**</span></span>|<span data-ttu-id="518aa-179">Pluraliza ou singulariza automaticamente nomes de classe e de membro.</span><span class="sxs-lookup"><span data-stu-id="518aa-179">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="518aa-180">Essa opção só está disponível na versão em inglês  dos EUA.</span><span class="sxs-lookup"><span data-stu-id="518aa-180">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="518aa-181">**/serialization:** *\<option>*</span><span class="sxs-lookup"><span data-stu-id="518aa-181">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="518aa-182">Gera classes serializáveis.</span><span class="sxs-lookup"><span data-stu-id="518aa-182">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="518aa-183">Valid *\<option>*: None, Unidirectional.</span><span class="sxs-lookup"><span data-stu-id="518aa-183">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="518aa-184">Valor padrão: Nenhum.</span><span class="sxs-lookup"><span data-stu-id="518aa-184">Default value: None.</span></span><br /><br /> <span data-ttu-id="518aa-185">Para obter mais informações, consulte [Serialização](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span><span class="sxs-lookup"><span data-stu-id="518aa-185">For more information, see [Serialization](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="518aa-186">**Arquivo de Entrada**</span><span class="sxs-lookup"><span data-stu-id="518aa-186">**Input File**</span></span>  
  
|<span data-ttu-id="518aa-187">Opção</span><span class="sxs-lookup"><span data-stu-id="518aa-187">Option</span></span>|<span data-ttu-id="518aa-188">Descrição</span><span class="sxs-lookup"><span data-stu-id="518aa-188">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="518aa-189">**\<input file>**</span><span class="sxs-lookup"><span data-stu-id="518aa-189">**\<input file>**</span></span>|<span data-ttu-id="518aa-190">Especifica um arquivo .mdf do SQL Server Express, um arquivo .sdf do [!INCLUDE[ssEW](../../../includes/ssew-md.md)] ou um arquivo intermediário .dbml.</span><span class="sxs-lookup"><span data-stu-id="518aa-190">Specifies a SQL Server Express .mdf file, a [!INCLUDE[ssEW](../../../includes/ssew-md.md)] .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="518aa-191">Comentários</span><span class="sxs-lookup"><span data-stu-id="518aa-191">Remarks</span></span>  
 <span data-ttu-id="518aa-192">A funcionalidade SqlMetal envolve, na realidade, duas etapas:</span><span class="sxs-lookup"><span data-stu-id="518aa-192">SqlMetal functionality actually involves two steps:</span></span>  
  
-   <span data-ttu-id="518aa-193">Extraindo os metadados do banco de dados para um arquivo. dbml.</span><span class="sxs-lookup"><span data-stu-id="518aa-193">Extracting the metadata of the database into a .dbml file.</span></span>  
  
-   <span data-ttu-id="518aa-194">Gerando um arquivo de saída do código.</span><span class="sxs-lookup"><span data-stu-id="518aa-194">Generating a code output file.</span></span>  
  
     <span data-ttu-id="518aa-195">Usando-se as opções de linha de comando apropriadas, é possível produzir o código-fonte do [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] ou do C# ou produzir um arquivo de mapeamento XML.</span><span class="sxs-lookup"><span data-stu-id="518aa-195">By using the appropriate command-line options, you can produce [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="518aa-196">Para extrair os metadados de um arquivo .mdf, você deve especificar o nome do arquivo .mdf depois de todas as outras opções.</span><span class="sxs-lookup"><span data-stu-id="518aa-196">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="518aa-197">Se nenhum **/server** for especificado, **localhost/sqlexpress** será suposto.</span><span class="sxs-lookup"><span data-stu-id="518aa-197">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 [!INCLUDE[sqprsqext](../../../includes/sqprsqext-md.md)]<span data-ttu-id="518aa-198"> acionará uma exceção se uma ou mais das seguintes condições forem verdadeiras:</span><span class="sxs-lookup"><span data-stu-id="518aa-198"> throws an exception if one or more of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="518aa-199">SqlMetal tenta extrair um procedimento armazenado que se chama.</span><span class="sxs-lookup"><span data-stu-id="518aa-199">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
-   <span data-ttu-id="518aa-200">O nível de aninhamento de um procedimento armazenado, função ou uma exibição excede 32.</span><span class="sxs-lookup"><span data-stu-id="518aa-200">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="518aa-201">SqlMetal captura essa exceção e a relata como um aviso.</span><span class="sxs-lookup"><span data-stu-id="518aa-201">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="518aa-202">Para especificar um nome do arquivo de entrada, adicione o nome do arquivo à linha de comando como o arquivo de entrada.</span><span class="sxs-lookup"><span data-stu-id="518aa-202">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="518aa-203">Não há suporte para a inclusão do nome de arquivo na cadeia de conexão (usando a opção **/conn**).</span><span class="sxs-lookup"><span data-stu-id="518aa-203">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="518aa-204">Exemplos</span><span class="sxs-lookup"><span data-stu-id="518aa-204">Examples</span></span>  
 <span data-ttu-id="518aa-205">Gera um arquivo. dbml que inclui metadados SQL extraídos:</span><span class="sxs-lookup"><span data-stu-id="518aa-205">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="518aa-206">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span><span class="sxs-lookup"><span data-stu-id="518aa-206">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="518aa-207">Gera um arquivo. dbml que inclui metadados SQL extraídos de um arquivo .mdf usando-se o SQL Server Express:</span><span class="sxs-lookup"><span data-stu-id="518aa-207">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="518aa-208">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span><span class="sxs-lookup"><span data-stu-id="518aa-208">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="518aa-209">Gera um arquivo. dbml que inclui metadados SQL extraídos do SQL Server Express:</span><span class="sxs-lookup"><span data-stu-id="518aa-209">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="518aa-210">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="518aa-210">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="518aa-211">Gera o código-fonte com base em um arquivo de metadados .dbml:</span><span class="sxs-lookup"><span data-stu-id="518aa-211">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="518aa-212">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span><span class="sxs-lookup"><span data-stu-id="518aa-212">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="518aa-213">Gera o código-fonte com base nos metadados SQL diretamente:</span><span class="sxs-lookup"><span data-stu-id="518aa-213">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="518aa-214">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span><span class="sxs-lookup"><span data-stu-id="518aa-214">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="518aa-215">Ao usar a opção **/pluralize** com o banco de dados de exemplo Northwind, observe o comportamento a seguir.</span><span class="sxs-lookup"><span data-stu-id="518aa-215">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="518aa-216">Quando SqlMetal cria nomes de tipo de linha para tabelas, os nomes de tabela são singulares.</span><span class="sxs-lookup"><span data-stu-id="518aa-216">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="518aa-217">Quando ele cria propriedades <xref:System.Data.Linq.DataContext> para tabelas, os nomes de tabela serão plurais.</span><span class="sxs-lookup"><span data-stu-id="518aa-217">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="518aa-218">Coincidentemente, as tabelas no banco de dados de exemplo Northwind já são plurais.</span><span class="sxs-lookup"><span data-stu-id="518aa-218">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="518aa-219">Por isso, você não vê essa parte funcionando.</span><span class="sxs-lookup"><span data-stu-id="518aa-219">Therefore, you do not see that part working.</span></span> <span data-ttu-id="518aa-220">Embora seja uma prática comum nomear tabelas de banco de dados singulares, também é uma prática comum no .NET nomear as coleções plurais.</span><span class="sxs-lookup"><span data-stu-id="518aa-220">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="518aa-221">Consulte também</span><span class="sxs-lookup"><span data-stu-id="518aa-221">See Also</span></span>  
 <span data-ttu-id="518aa-222">[Como gerar o modelo de objeto em Visual Basic ou C#](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md) </span><span class="sxs-lookup"><span data-stu-id="518aa-222">[How to: Generate the Object Model in Visual Basic or C#](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md) </span></span>  
 <span data-ttu-id="518aa-223">[Geração de código em LINQ to SQL](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md) </span><span class="sxs-lookup"><span data-stu-id="518aa-223">[Code Generation in LINQ to SQL](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md) </span></span>  
 [<span data-ttu-id="518aa-224">Mapeamento Externo</span><span class="sxs-lookup"><span data-stu-id="518aa-224">External Mapping</span></span>](../../../docs/framework/data/adonet/sql/linq/external-mapping.md)

