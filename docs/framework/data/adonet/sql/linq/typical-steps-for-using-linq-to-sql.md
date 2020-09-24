---
title: Etapas comuns de uso do LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: dc8c4be1e895ee5c4c7947e6311e5bf71008490f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164254"
---
# <a name="typical-steps-for-using-linq-to-sql"></a><span data-ttu-id="32a5c-102">Etapas comuns de uso do LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="32a5c-102">Typical Steps for Using LINQ to SQL</span></span>

<span data-ttu-id="32a5c-103">Para implementar um aplicativo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], siga as etapas descritas mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="32a5c-103">To implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application, you follow the steps described later in this topic.</span></span> <span data-ttu-id="32a5c-104">Observe que várias etapas são opcionais.</span><span class="sxs-lookup"><span data-stu-id="32a5c-104">Note that many steps are optional.</span></span> <span data-ttu-id="32a5c-105">É muito provável que você possa usar o modelo de objeto em seu estado padrão.</span><span class="sxs-lookup"><span data-stu-id="32a5c-105">It is very possible that you can use your object model in its default state.</span></span>  
  
 <span data-ttu-id="32a5c-106">Para um início realmente rápido, use o Object Relational Designer para criar o modelo de objeto e começar a codificar suas consultas.</span><span class="sxs-lookup"><span data-stu-id="32a5c-106">For a really fast start, use the Object Relational Designer to create your object model and start coding your queries.</span></span>  
  
## <a name="creating-the-object-model"></a><span data-ttu-id="32a5c-107">Criando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="32a5c-107">Creating the Object Model</span></span>  

 <span data-ttu-id="32a5c-108">A primeira etapa é criar um modelo de objeto a partir dos metadados de um banco de dados relacional existente.</span><span class="sxs-lookup"><span data-stu-id="32a5c-108">The first step is to create an object model from the metadata of an existing relational database.</span></span> <span data-ttu-id="32a5c-109">O modelo de objeto representa o banco de dados de acordo com a linguagem de programação do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="32a5c-109">The object model represents the database according to the programming language of the developer.</span></span> <span data-ttu-id="32a5c-110">Para obter mais informações, consulte [o modelo de objeto LINQ to SQL](the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="32a5c-110">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
### <a name="1-select-a-tool-to-create-the-model"></a><span data-ttu-id="32a5c-111">1. Selecione uma ferramenta para criar o modelo.</span><span class="sxs-lookup"><span data-stu-id="32a5c-111">1. Select a tool to create the model.</span></span>  

 <span data-ttu-id="32a5c-112">Três ferramentas estão disponíveis para criar o modelo.</span><span class="sxs-lookup"><span data-stu-id="32a5c-112">Three tools are available for creating the model.</span></span>  
  
- <span data-ttu-id="32a5c-113">O Object Relational Designer</span><span class="sxs-lookup"><span data-stu-id="32a5c-113">The Object Relational Designer</span></span>  
  
     <span data-ttu-id="32a5c-114">Esse designer fornece uma interface de usuário perfeita para criar um modelo de objeto a partir de um banco de dados existente.</span><span class="sxs-lookup"><span data-stu-id="32a5c-114">This designer provides a rich user interface for creating an object model from an existing database.</span></span> <span data-ttu-id="32a5c-115">Essa ferramenta faz parte do IDE do Visual Studio e é mais adequada para bancos de dados pequenos ou médios.</span><span class="sxs-lookup"><span data-stu-id="32a5c-115">This tool is part of the Visual Studio IDE, and is best suited to small or medium databases.</span></span>  
  
- <span data-ttu-id="32a5c-116">A ferramenta de geração de código SQLMetal</span><span class="sxs-lookup"><span data-stu-id="32a5c-116">The SQLMetal code-generation tool</span></span>  
  
     <span data-ttu-id="32a5c-117">Esse utilitário de linha de comando fornece um conjunto ligeiramente diferente de opções do o/R Designer.</span><span class="sxs-lookup"><span data-stu-id="32a5c-117">This command-line utility provides a slightly different set of options from the O/R Designer.</span></span> <span data-ttu-id="32a5c-118">A modelagem de grandes bancos de dados é mais bem efetuada com essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="32a5c-118">Modeling large databases is best done by using this tool.</span></span> <span data-ttu-id="32a5c-119">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="32a5c-119">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
- <span data-ttu-id="32a5c-120">Um editor de código</span><span class="sxs-lookup"><span data-stu-id="32a5c-120">A code editor</span></span>  
  
     <span data-ttu-id="32a5c-121">Você pode escrever seu próprio código usando o editor de código do Visual Studio ou outro editor.</span><span class="sxs-lookup"><span data-stu-id="32a5c-121">You can write your own code by using either the Visual Studio code editor or another editor.</span></span> <span data-ttu-id="32a5c-122">Não recomendamos essa abordagem, que pode ser propenso a erros, quando você tem um banco de dados existente e pode usar o o/R Designer ou a ferramenta SqlMetal.</span><span class="sxs-lookup"><span data-stu-id="32a5c-122">We do not recommend this approach, which can be prone to errors, when you have an existing database and can use either the O/R Designer or the SQLMetal tool.</span></span> <span data-ttu-id="32a5c-123">Entretanto, o editor de códigos pode ser útil para refinar ou modificar o código que você já gerou usando outras ferramentas.</span><span class="sxs-lookup"><span data-stu-id="32a5c-123">However, the code editor can be valuable for refining or modifying code you have already generated by using other tools.</span></span> <span data-ttu-id="32a5c-124">Para obter mais informações, consulte [como: Personalizar classes de entidade usando o editor de código](how-to-customize-entity-classes-by-using-the-code-editor.md).</span><span class="sxs-lookup"><span data-stu-id="32a5c-124">For more information, see [How to: Customize Entity Classes by Using the Code Editor](how-to-customize-entity-classes-by-using-the-code-editor.md).</span></span>  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a><span data-ttu-id="32a5c-125">2. Selecione o tipo de código que você deseja gerar.</span><span class="sxs-lookup"><span data-stu-id="32a5c-125">2. Select the kind of code you want to generate.</span></span>  
  
- <span data-ttu-id="32a5c-126">Um arquivo de código-fonte do C# ou Visual Basic para mapeamento baseado em atributo.</span><span class="sxs-lookup"><span data-stu-id="32a5c-126">A C# or Visual Basic source code file for attribute-based mapping.</span></span>  
  
     <span data-ttu-id="32a5c-127">Em seguida, você inclui esse arquivo de código em seu projeto do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="32a5c-127">You then include this code file in your Visual Studio project.</span></span> <span data-ttu-id="32a5c-128">Para obter mais informações, consulte [mapeamento baseado em atributo](attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="32a5c-128">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
- <span data-ttu-id="32a5c-129">Um arquivo XML para mapeamento externo.</span><span class="sxs-lookup"><span data-stu-id="32a5c-129">An XML file for external mapping.</span></span>  
  
     <span data-ttu-id="32a5c-130">Usando essa abordagem, você pode manter os metadados de mapeamento fora de seu código de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="32a5c-130">By using this approach, you can keep the mapping metadata out of your application code.</span></span> <span data-ttu-id="32a5c-131">Para obter mais informações, consulte [mapeamento externo](external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="32a5c-131">For more information, see [External Mapping](external-mapping.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="32a5c-132">O o/R Designer não oferece suporte à geração de arquivos de mapeamento externos.</span><span class="sxs-lookup"><span data-stu-id="32a5c-132">The O/R Designer does not support the generation of external mapping files.</span></span> <span data-ttu-id="32a5c-133">Você deve usar a ferramenta SQLMetal para implementar esse recurso.</span><span class="sxs-lookup"><span data-stu-id="32a5c-133">You must use the SQLMetal tool to implement this feature.</span></span>  
  
- <span data-ttu-id="32a5c-134">Um arquivo DBML, que você pode modificar antes de gerar um arquivo de código final.</span><span class="sxs-lookup"><span data-stu-id="32a5c-134">A DBML file, which you can modify before generating a final code file.</span></span>  
  
     <span data-ttu-id="32a5c-135">Esse é um recurso avançado.</span><span class="sxs-lookup"><span data-stu-id="32a5c-135">This is an advanced feature.</span></span>  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a><span data-ttu-id="32a5c-136">3. Refine o arquivo de código para refletir as necessidades do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="32a5c-136">3. Refine the code file to reflect the needs of your application.</span></span>  

 <span data-ttu-id="32a5c-137">Para essa finalidade, você pode usar o o/R Designer ou o editor de código.</span><span class="sxs-lookup"><span data-stu-id="32a5c-137">For this purpose, you can use either the O/R Designer or the code editor.</span></span>  
  
## <a name="using-the-object-model"></a><span data-ttu-id="32a5c-138">Usando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="32a5c-138">Using the Object Model</span></span>  

 <span data-ttu-id="32a5c-139">A ilustração a seguir mostra a relação entre o desenvolvedor e os dados em um cenário de duas camadas.</span><span class="sxs-lookup"><span data-stu-id="32a5c-139">The following illustration shows the relationship between the developer and the data in a two-tier scenario.</span></span> <span data-ttu-id="32a5c-140">Para outros cenários, consulte [N-tier e aplicativos remotos com LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="32a5c-140">For other scenarios, see [N-Tier and Remote Applications with LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md).</span></span>  
  
 ![Captura de tela que mostra o modelo de objeto LINQ.](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 <span data-ttu-id="32a5c-142">Agora que você tem o modelo de objeto, você descreve as solicitações de informações e manipula dados dentro desse modelo.</span><span class="sxs-lookup"><span data-stu-id="32a5c-142">Now that you have the object model, you describe information requests and manipulate data within that model.</span></span> <span data-ttu-id="32a5c-143">Você pensa em termos de objetos e propriedades no seu modelo de objeto e não em termos de linhas e colunas do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="32a5c-143">You think in terms of the objects and properties in your object model and not in terms of the rows and columns of the database.</span></span> <span data-ttu-id="32a5c-144">Você não lida diretamente com o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="32a5c-144">You do not deal directly with the database.</span></span>  
  
 <span data-ttu-id="32a5c-145">Quando você instruir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a executar uma consulta que você descreveu ou chamar `SubmitChanges()` em dados que você manipulou, o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se comunicará com o Database no idioma do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="32a5c-145">When you instruct [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to either execute a query that you have described or call `SubmitChanges()` on data that you have manipulated, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] communicates with the database in the language of the database.</span></span>  
  
 <span data-ttu-id="32a5c-146">A seguir estão etapas comuns de uso do modelo de objeto que você criou.</span><span class="sxs-lookup"><span data-stu-id="32a5c-146">The following represents typical steps for using the object model that you have created.</span></span>  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a><span data-ttu-id="32a5c-147">1. crie consultas para recuperar informações do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="32a5c-147">1. Create queries to retrieve information from the database.</span></span>  

 <span data-ttu-id="32a5c-148">Para obter mais informações, consulte [conceitos de consulta](query-concepts.md) e exemplos de [consulta](query-examples.md).</span><span class="sxs-lookup"><span data-stu-id="32a5c-148">For more information, see [Query Concepts](query-concepts.md) and [Query Examples](query-examples.md).</span></span>  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a><span data-ttu-id="32a5c-149">2. substituir os comportamentos padrão para inserir, atualizar e excluir.</span><span class="sxs-lookup"><span data-stu-id="32a5c-149">2. Override default behaviors for Insert, Update, and Delete.</span></span>  

 <span data-ttu-id="32a5c-150">Essa etapa é opcional.</span><span class="sxs-lookup"><span data-stu-id="32a5c-150">This step is optional.</span></span> <span data-ttu-id="32a5c-151">Para obter mais informações, consulte [Personalizando as operações de inserção, atualização e exclusão](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="32a5c-151">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a><span data-ttu-id="32a5c-152">3. Defina as opções apropriadas para detectar e relatar conflitos de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="32a5c-152">3. Set appropriate options to detect and report concurrency conflicts.</span></span>  

 <span data-ttu-id="32a5c-153">Você pode deixar o modelo com seus valores padrão para manipular conflitos de simultaneidade, ou pode alterá-lo para atender aos seus propósitos.</span><span class="sxs-lookup"><span data-stu-id="32a5c-153">You can leave your model with its default values for handling concurrency conflicts, or you can change it to suit your purposes.</span></span> <span data-ttu-id="32a5c-154">Para obter mais informações, consulte [como especificar quais membros são testados para conflitos de simultaneidade](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) e [como especificar quando exceções de simultaneidade são geradas](how-to-specify-when-concurrency-exceptions-are-thrown.md).</span><span class="sxs-lookup"><span data-stu-id="32a5c-154">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) and [How to: Specify When Concurrency Exceptions are Thrown](how-to-specify-when-concurrency-exceptions-are-thrown.md).</span></span>  
  
### <a name="4-establish-an-inheritance-hierarchy"></a><span data-ttu-id="32a5c-155">4. estabeleça uma hierarquia de herança.</span><span class="sxs-lookup"><span data-stu-id="32a5c-155">4. Establish an inheritance hierarchy.</span></span>  

 <span data-ttu-id="32a5c-156">Essa etapa é opcional.</span><span class="sxs-lookup"><span data-stu-id="32a5c-156">This step is optional.</span></span> <span data-ttu-id="32a5c-157">Para obter mais informações, consulte [suporte à herança](inheritance-support.md).</span><span class="sxs-lookup"><span data-stu-id="32a5c-157">For more information, see [Inheritance Support](inheritance-support.md).</span></span>  
  
### <a name="5-provide-an-appropriate-user-interface"></a><span data-ttu-id="32a5c-158">5. forneça uma interface do usuário apropriada.</span><span class="sxs-lookup"><span data-stu-id="32a5c-158">5. Provide an appropriate user interface.</span></span>  

 <span data-ttu-id="32a5c-159">Esta etapa é opcional, e depende de como o aplicativo será usado.</span><span class="sxs-lookup"><span data-stu-id="32a5c-159">This step is optional, and depends on how your application will be used.</span></span>  
  
### <a name="6-debug-and-test-your-application"></a><span data-ttu-id="32a5c-160">6. depure e teste seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="32a5c-160">6. Debug and test your application.</span></span>  

 <span data-ttu-id="32a5c-161">Para obter mais informações, consulte [depuração de suporte](debugging-support.md).</span><span class="sxs-lookup"><span data-stu-id="32a5c-161">For more information, see [Debugging Support](debugging-support.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a5c-162">Confira também</span><span class="sxs-lookup"><span data-stu-id="32a5c-162">See also</span></span>

- [<span data-ttu-id="32a5c-163">Introdução</span><span class="sxs-lookup"><span data-stu-id="32a5c-163">Getting Started</span></span>](getting-started.md)
- [<span data-ttu-id="32a5c-164">Criando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="32a5c-164">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="32a5c-165">Procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="32a5c-165">Stored Procedures</span></span>](stored-procedures.md)
