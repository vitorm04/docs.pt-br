---
title: Criar um projeto LINQ to DataSet no Visual Studio
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 22763d3b9581d09d7bdda0c09480f8d36bb8e2ec
ms.sourcegitcommit: 4bca8f7e172fd019ef437a4803bf5895c6bc4781
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2018
ms.locfileid: "50980723"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="43277-102">Como: criar um projeto LINQ to DataSet no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="43277-102">How to: Create a LINQ to DataSet project In Visual Studio</span></span>

<span data-ttu-id="43277-103">Os diferentes tipos de projetos LINQ exigem determinados namespaces importados (Visual Basic) e referências de assembly ou [usando](../../../csharp/language-reference/keywords/using-directive.md) diretivas (c#).</span><span class="sxs-lookup"><span data-stu-id="43277-103">The different types of LINQ projects require certain assembly references and imported namespaces (Visual Basic) or [using](../../../csharp/language-reference/keywords/using-directive.md) directives (C#).</span></span> <span data-ttu-id="43277-104">O requisito mínimo para LINQ é uma referência a *dll* e uma `using` diretiva <xref:System.Linq>.</span><span class="sxs-lookup"><span data-stu-id="43277-104">The minimum requirement for LINQ is a reference to *System.Core.dll* and a `using` directive for <xref:System.Linq>.</span></span>

<span data-ttu-id="43277-105">Esses requisitos são fornecidos por padrão, se você criar um novo console aplicativo projeto c# no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="43277-105">These requirements are supplied by default if you create a new C# console app project in Visual Studio 2017.</span></span> <span data-ttu-id="43277-106">Se você estiver atualizando um projeto de uma versão anterior do Visual Studio, talvez você precise fornecer essas referências relacionadas a LINQ manualmente.</span><span class="sxs-lookup"><span data-stu-id="43277-106">If you're upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span>

<span data-ttu-id="43277-107">LINQ to DataSet requer duas referências adicionais ao *dll* e *DataSetExtensions. dll*.</span><span class="sxs-lookup"><span data-stu-id="43277-107">LINQ to DataSet requires two additional references to *System.Data.dll* and *System.Data.DataSetExtensions.dll*.</span></span>

> [!NOTE]
> <span data-ttu-id="43277-108">Se você estiver compilando em um prompt de comando, deverá manualmente referenciar as DLLs relacionadas a LINQ no *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span><span class="sxs-lookup"><span data-stu-id="43277-108">If you're building from a command prompt, you must manually reference the LINQ-related DLLs in *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span></span>

## <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="43277-109">Para ativar a funcionalidade LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="43277-109">To enable LINQ to DataSet functionality</span></span>

<span data-ttu-id="43277-110">Siga estas etapas para habilitar o LINQ para funcionalidade de conjunto de dados em um projeto existente.</span><span class="sxs-lookup"><span data-stu-id="43277-110">Follow these steps to enable LINQ to DataSet functionality in an existing project.</span></span>

1. <span data-ttu-id="43277-111">Adicione referências aos **System. Core**, **System. Data**, e **DataSetExtensions**.</span><span class="sxs-lookup"><span data-stu-id="43277-111">Add references to **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span>

   <span data-ttu-id="43277-112">Na **Gerenciador de soluções**, clique com botão direito no **referências** nó e selecione **Add Reference**.</span><span class="sxs-lookup"><span data-stu-id="43277-112">In **Solution Explorer**, right-click on the **References** node and select **Add Reference**.</span></span> <span data-ttu-id="43277-113">No **Gerenciador de referências** caixa de diálogo, selecione **System. Core**, **System. Data**, e **DataSetExtensions**.</span><span class="sxs-lookup"><span data-stu-id="43277-113">In the **Reference Manager** dialog box, select **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span> <span data-ttu-id="43277-114">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="43277-114">Select **OK**.</span></span>

1. <span data-ttu-id="43277-115">Adicione [usando](../../../csharp/language-reference/keywords/using-directive.md) diretivas (ou [instruções Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) no Visual Basic) para **System. Data** e **System. LINQ**.</span><span class="sxs-lookup"><span data-stu-id="43277-115">Add [using](../../../csharp/language-reference/keywords/using-directive.md) directives (or [Imports statements](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) in Visual Basic) for **System.Data** and **System.Linq**.</span></span>

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. <span data-ttu-id="43277-116">Opcionalmente, adicione uma `using` diretiva (ou `Imports` instrução) para **Common** ou **System.Data.SqlClient**, dependendo de como você se conecta ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="43277-116">Optionally, add a `using` directive (or `Imports` statement) for **System.Data.Common** or **System.Data.SqlClient**, depending on how you connect to the database.</span></span>

## <a name="see-also"></a><span data-ttu-id="43277-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43277-117">See also</span></span>

- [<span data-ttu-id="43277-118">Introdução ao LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="43277-118">Get started with LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
