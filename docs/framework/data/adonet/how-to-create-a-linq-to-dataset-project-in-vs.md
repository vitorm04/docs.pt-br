---
title: Criar um projeto LINQ to DataSet no Visual Studio
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 8b905c65575c3c567459d843b2a5d1606bc63228
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783769"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="37773-102">Como: Criar um projeto LINQ to DataSet no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="37773-102">How to: Create a LINQ to DataSet project In Visual Studio</span></span>

<span data-ttu-id="37773-103">Os diferentes tipos de projetos LINQ exigem determinadas referências de assembly e namespaces importados (Visual Basic) ou C# [usando](../../../csharp/language-reference/keywords/using-directive.md) diretivas ().</span><span class="sxs-lookup"><span data-stu-id="37773-103">The different types of LINQ projects require certain assembly references and imported namespaces (Visual Basic) or [using](../../../csharp/language-reference/keywords/using-directive.md) directives (C#).</span></span> <span data-ttu-id="37773-104">O requisito mínimo para LINQ é uma referência a *System. Core. dll* e a `using` uma diretiva <xref:System.Linq>para.</span><span class="sxs-lookup"><span data-stu-id="37773-104">The minimum requirement for LINQ is a reference to *System.Core.dll* and a `using` directive for <xref:System.Linq>.</span></span>

<span data-ttu-id="37773-105">Esses requisitos são fornecidos por padrão se você criar um novo C# projeto de aplicativo de console no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="37773-105">These requirements are supplied by default if you create a new C# console app project in Visual Studio 2017.</span></span> <span data-ttu-id="37773-106">Se você estiver atualizando um projeto de uma versão anterior do Visual Studio, talvez seja necessário fornecer essas referências relacionadas ao LINQ manualmente.</span><span class="sxs-lookup"><span data-stu-id="37773-106">If you're upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span>

<span data-ttu-id="37773-107">LINQ to DataSet requer duas referências adicionais a *System. Data. dll* e *System. Data. DataSetExtensions. dll*.</span><span class="sxs-lookup"><span data-stu-id="37773-107">LINQ to DataSet requires two additional references to *System.Data.dll* and *System.Data.DataSetExtensions.dll*.</span></span>

> [!NOTE]
> <span data-ttu-id="37773-108">Se você estiver criando a partir de um prompt de comando, deverá referenciar manualmente as DLLs relacionadas ao LINQ no *%programfiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span><span class="sxs-lookup"><span data-stu-id="37773-108">If you're building from a command prompt, you must manually reference the LINQ-related DLLs in *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span></span>

## <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="37773-109">Para ativar a funcionalidade LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="37773-109">To enable LINQ to DataSet functionality</span></span>

<span data-ttu-id="37773-110">Siga estas etapas para habilitar LINQ to DataSet funcionalidade em um projeto existente.</span><span class="sxs-lookup"><span data-stu-id="37773-110">Follow these steps to enable LINQ to DataSet functionality in an existing project.</span></span>

1. <span data-ttu-id="37773-111">Adicione referências a **System. Core**, **System. Data**e **System. Data. DataSetExtensions**.</span><span class="sxs-lookup"><span data-stu-id="37773-111">Add references to **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span>

   <span data-ttu-id="37773-112">Em **Gerenciador de soluções**, clique com o botão direito do mouse no nó **referências** e selecione **Adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="37773-112">In **Solution Explorer**, right-click on the **References** node and select **Add Reference**.</span></span> <span data-ttu-id="37773-113">Na caixa de diálogo **Gerenciador de referências** , selecione **System. Core**, **System. Data**e **System. Data. DataSetExtensions**.</span><span class="sxs-lookup"><span data-stu-id="37773-113">In the **Reference Manager** dialog box, select **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span> <span data-ttu-id="37773-114">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="37773-114">Select **OK**.</span></span>

1. <span data-ttu-id="37773-115">Adicione [usando](../../../csharp/language-reference/keywords/using-directive.md) diretivas (ou [instruções Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) em Visual Basic) para **System. Data** e **System. Linq**.</span><span class="sxs-lookup"><span data-stu-id="37773-115">Add [using](../../../csharp/language-reference/keywords/using-directive.md) directives (or [Imports statements](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) in Visual Basic) for **System.Data** and **System.Linq**.</span></span>

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. <span data-ttu-id="37773-116">Opcionalmente, adicione uma `using` diretiva (ou `Imports` instrução) para **System. Data. Common** ou **System. Data. SqlClient**, dependendo de como você se conecta ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="37773-116">Optionally, add a `using` directive (or `Imports` statement) for **System.Data.Common** or **System.Data.SqlClient**, depending on how you connect to the database.</span></span>

## <a name="see-also"></a><span data-ttu-id="37773-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37773-117">See also</span></span>

- [<span data-ttu-id="37773-118">Introdução ao LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="37773-118">Get started with LINQ to DataSet</span></span>](getting-started-linq-to-dataset.md)
