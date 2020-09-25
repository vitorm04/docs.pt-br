---
title: Como fornecer uma caixa de diálogo de progresso para operações de arquivo – guia de programação C#
description: Saiba como fornecer uma caixa de diálogo de progresso para operações de arquivo usando o método CopyFile (String, String, UIOption).
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 5d16aeb3a5394ca250e4a5e26074db797c54216d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185880"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="e1326-103">Como fornecer uma caixa de diálogo de progresso para operações de arquivo (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="e1326-103">How to provide a progress dialog box for file operations (C# Programming Guide)</span></span>

<span data-ttu-id="e1326-104">Você pode fornecer uma caixa de diálogo padrão que mostra o andamento em operações de arquivos no Windows se você usar o método <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> no namespace <xref:Microsoft.VisualBasic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e1326-104">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="e1326-105">Para adicionar uma referência no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e1326-105">To add a reference in Visual Studio</span></span>  
  
1. <span data-ttu-id="e1326-106">Na barra de menus, escolha **Projeto**, **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="e1326-106">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="e1326-107">A caixa de diálogo **Gerenciador de Referências** é exibida.</span><span class="sxs-lookup"><span data-stu-id="e1326-107">The **Reference Manager** dialog box appears.</span></span>  
  
2. <span data-ttu-id="e1326-108">Na área **Assemblies**, escolha **Framework** se ele ainda não estiver escolhido.</span><span class="sxs-lookup"><span data-stu-id="e1326-108">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
3. <span data-ttu-id="e1326-109">Na lista de nomes, marque a caixa de seleção **Microsoft.VisualBasic** e, em seguida, escolha o botão **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="e1326-109">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1326-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1326-110">Example</span></span>  

 <span data-ttu-id="e1326-111">O código a seguir copia o diretório que `sourcePath` especifica, para o diretório que `destinationPath` especifica.</span><span class="sxs-lookup"><span data-stu-id="e1326-111">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="e1326-112">Esse código também fornece uma caixa de diálogo padrão que mostra a quantidade estimada de tempo que resta antes da conclusão da operação.</span><span class="sxs-lookup"><span data-stu-id="e1326-112">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="e1326-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="e1326-113">See also</span></span>

- [<span data-ttu-id="e1326-114">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="e1326-114">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
