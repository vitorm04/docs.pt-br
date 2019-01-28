---
title: 'Como: fornecer uma caixa de diálogo de progresso para operações de arquivo – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: ab268c30af6b5eefe84ade852c679535c1e48068
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597262"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="e6e12-102">Como: fornecer uma caixa de diálogo de progresso para operações de arquivo (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="e6e12-102">How to: Provide a Progress Dialog Box for File Operations (C# Programming Guide)</span></span>
<span data-ttu-id="e6e12-103">Você pode fornecer uma caixa de diálogo padrão que mostra o andamento em operações de arquivos no Windows se você usar o método <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> no namespace <xref:Microsoft.VisualBasic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6e12-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="e6e12-104">Para adicionar uma referência no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e6e12-104">To add a reference in Visual Studio</span></span>  
  
1.  <span data-ttu-id="e6e12-105">Na barra de menus, escolha **Projeto**, **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="e6e12-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="e6e12-106">A caixa de diálogo **Gerenciador de Referências** é exibida.</span><span class="sxs-lookup"><span data-stu-id="e6e12-106">The **Reference Manager** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="e6e12-107">Na área **Assemblies**, escolha **Framework** se ele ainda não estiver escolhido.</span><span class="sxs-lookup"><span data-stu-id="e6e12-107">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
3.  <span data-ttu-id="e6e12-108">Na lista de nomes, marque a caixa de seleção **Microsoft.VisualBasic** e, em seguida, escolha o botão **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="e6e12-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6e12-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e6e12-109">Example</span></span>  
 <span data-ttu-id="e6e12-110">O código a seguir copia o diretório que `sourcePath` especifica, para o diretório que `destinationPath` especifica.</span><span class="sxs-lookup"><span data-stu-id="e6e12-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="e6e12-111">Esse código também fornece uma caixa de diálogo padrão que mostra a quantidade estimada de tempo que resta antes da conclusão da operação.</span><span class="sxs-lookup"><span data-stu-id="e6e12-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e6e12-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6e12-112">See also</span></span>

- [<span data-ttu-id="e6e12-113">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="e6e12-113">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
