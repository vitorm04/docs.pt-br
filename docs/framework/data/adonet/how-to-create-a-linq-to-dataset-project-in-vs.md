---
title: Como criar um projeto LINQ to DataSet no Visual Studio
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6710d3e9bf52ff10ee8dd545161f0858001f2c40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="0f4cc-102">Como criar um projeto LINQ to DataSet no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0f4cc-102">How to: Create a LINQ to DataSet Project In Visual Studio</span></span>
<span data-ttu-id="0f4cc-103">Os diferentes tipos de projetos do [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] exigem determinados namespaces importados (Visual Basic) ou diretivas `using` (C#) e referências.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-103">The different types of [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] projects require certain imported namespaces (Visual Basic) or `using` directives (C#) and references.</span></span> <span data-ttu-id="0f4cc-104">O requisito mínimo é uma referência ao System.Core.dll e uma diretiva `using` para <xref:System.Linq>.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-104">The minimum requirement is a reference to System.Core.dll and a `using` directive for <xref:System.Linq>.</span></span> <span data-ttu-id="0f4cc-105">Por padrão, eles serão fornecidos se você criar um novo projeto [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0f4cc-105">By default, these are supplied if you create a new [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] project.</span></span> <span data-ttu-id="0f4cc-106">O [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] também exige uma referência para System.Data.dll e System.Data.DataSetExtensions.dll e uma diretiva `Imports` (Visual Basic) ou `using` (C#).</span><span class="sxs-lookup"><span data-stu-id="0f4cc-106">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] also requires a reference to System.Data.dll and System.Data.DataSetExtensions.dll and an `Imports` (Visual Basic) or `using` (C#) directive.</span></span>  
  
 <span data-ttu-id="0f4cc-107">Se você estiver atualizando um projeto de uma versão anterior do Visual Studio, poderá ter que fornecer manualmente essas referências relacionadas a LINQ.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-107">If you are upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span> <span data-ttu-id="0f4cc-108">Você também pode ter que definir manualmente o projeto para direcionar a versão 3.5 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-108">You might also have to manually set the project to target the .NET Framework version 3.5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f4cc-109">Se você estiver criando a partir de um prompt de comando, você deve referenciar manualmente as DLLs relacionadas a LINQ em `drive` **:**\Program Files\Reference Assemblies\Microsoft\Framework\v3.5.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-109">If you are building from a command prompt, you must manually reference the LINQ-related DLLs in `drive`**:**\Program Files\Reference Assemblies\Microsoft\Framework\v3.5.</span></span>  
  
### <a name="to-target-the-net-framework-35"></a><span data-ttu-id="0f4cc-110">Para direcionar o .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="0f4cc-110">To target the .NET Framework 3.5</span></span>  
  
1.  <span data-ttu-id="0f4cc-111">Em [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], crie um novo projeto do Visual Basic ou c#.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-111">In [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], create a new Visual Basic or C# project.</span></span> <span data-ttu-id="0f4cc-112">Como alternativa, você pode abrir um projeto Visual Basic ou c# que foi criado no Visual Studio 2005 e siga os prompts para convertê-lo para um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projeto.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-112">Alternatively, you can open a Visual Basic or C# project that was created in Visual Studio 2005 and follow the prompts to convert it to a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="0f4cc-113">Para um projeto c#, clique o **projeto** menu e clique **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-113">For a C# project, click the **Project** menu, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="0f4cc-114">No **aplicativo** página de propriedades, selecione o .NET Framework 3.5 no **Framework de destino** lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-114">In the **Application** property page, select .NET Framework 3.5 in the **Target Framework** drop-down list.</span></span>  
  
3.  <span data-ttu-id="0f4cc-115">Para um projeto do Visual Basic, clique o **projeto** menu e clique **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-115">For a Visual Basic project, click the **Project** menu, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="0f4cc-116">No **compilar** página de propriedades, clique em **opções avançadas de compilação** e, em seguida, selecione o .NET Framework 3.5 no **Framework de destino (todas as configurações)** lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-116">In the **Compile** property page, click **Advanced Compile Options** and then select .NET Framework 3.5 in the **Target Framework (all configurations)** drop-down list.</span></span>  
  
4.  <span data-ttu-id="0f4cc-117">No **projeto** menu, clique em **adicionar referência**, clique no **.NET** guia, role para baixo até **Core**, clique nele e, em seguida, clique em  **Okey**.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-117">On the **Project** menu, click **Add Reference**, click the **.NET** tab, scroll down to **System.Core**, click it, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="0f4cc-118">Adicione uma diretiva `using` ou um namespace importado para <xref:System.Linq> ao seu arquivo de código-fonte ou projeto.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-118">Add a `using` directive or imported namespace for <xref:System.Linq> to your source code file or project.</span></span>  
  
     <span data-ttu-id="0f4cc-119">Para obter mais informações, consulte [usando diretiva](~/docs/csharp/language-reference/keywords/using-directive.md) ou [como: Adicionar ou remover Namespaces importados (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="0f4cc-119">For more information, see [using Directive](~/docs/csharp/language-reference/keywords/using-directive.md) or [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
### <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="0f4cc-120">Para ativar a funcionalidade LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="0f4cc-120">To enable LINQ to DataSet functionality</span></span>  
  
1.  <span data-ttu-id="0f4cc-121">Se necessário, siga as etapas anteriores neste tópico para adicionar uma referência para o System.Core.dll e uma diretiva `using` ou o namespace importado para System.Linq.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-121">If necessary, follow the steps earlier in this topic to add a reference to System.Core.dll and a `using` directive or imported namespace for System.Linq.</span></span>  
  
2.  <span data-ttu-id="0f4cc-122">Em c# ou Visual Basic, clique no **projeto** menu e clique **adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-122">In C# or Visual Basic, click the **Project** menu, and then click **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="0f4cc-123">No **adicionar referência** caixa de diálogo, clique o **.NET** guia se não estiver na parte superior.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-123">In the **Add Reference** dialog box, click the **.NET** tab if it is not on top.</span></span> <span data-ttu-id="0f4cc-124">Role para baixo até **System. Data** e **System.Data.DataSetExtensions** e clicar neles.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-124">Scroll down to **System.Data** and **System.Data.DataSetExtensions** and click on them.</span></span> <span data-ttu-id="0f4cc-125">Clique o **Okey** botão.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-125">Click the **OK** button.</span></span>  
  
4.  <span data-ttu-id="0f4cc-126">Adicione uma diretiva `using` ou um namespace importado para <xref:System.Data> ao seu arquivo de código-fonte ou projeto.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-126">Add a `using` directive or imported namespace for <xref:System.Data> to your source code file or project.</span></span> <span data-ttu-id="0f4cc-127">Para obter mais informações, consulte [usando diretiva](~/docs/csharp/language-reference/keywords/using-directive.md) ou [como: Adicionar ou remover Namespaces importados (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="0f4cc-127">For more information, see [using Directive](~/docs/csharp/language-reference/keywords/using-directive.md) or [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
5.  <span data-ttu-id="0f4cc-128">Adicione uma referência ao System.Data.DataSetExtensions.dll para a funcionalidade LINQ to Dataset.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-128">Add a reference to System.Data.DataSetExtensions.dll for LINQ to Dataset functionality.</span></span> <span data-ttu-id="0f4cc-129">Adicione uma referência para System.Data.dll se ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-129">Add a reference to System.Data.dll if it does not already exist.</span></span>  
  
6.  <span data-ttu-id="0f4cc-130">Opcionalmente, adicione uma diretiva `using` ou um namespace importado para `System.Data.Common` ou `System.Data.SqlClient`, dependendo de como você se conecta ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-130">Optionally, add a `using` directive or imported namespace for `System.Data.Common` or `System.Data.SqlClient`, depending on how you connect to the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f4cc-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f4cc-131">See Also</span></span>  
 [<span data-ttu-id="0f4cc-132">Introdução</span><span class="sxs-lookup"><span data-stu-id="0f4cc-132">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
 [<span data-ttu-id="0f4cc-133">Introdução ao LINQ</span><span class="sxs-lookup"><span data-stu-id="0f4cc-133">Getting Started with LINQ</span></span>](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)
