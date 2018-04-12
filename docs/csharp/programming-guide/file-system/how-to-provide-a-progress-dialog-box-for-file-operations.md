---
title: Como fornecer uma caixa de diálogo de progresso para operações de arquivo (Guia de Programação em C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0ac68b5aa6014db87b4f7a269ef73d0608371bd8
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="24c2d-102">Como fornecer uma caixa de diálogo de progresso para operações de arquivo (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="24c2d-102">How to: Provide a Progress Dialog Box for File Operations (C# Programming Guide)</span></span>
<span data-ttu-id="24c2d-103">Você pode fornecer uma caixa de diálogo padrão que mostra o andamento em operações de arquivos no Windows se você usar o método <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> no namespace <xref:Microsoft.VisualBasic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="24c2d-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="24c2d-104">Para adicionar uma referência no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="24c2d-104">To add a reference in Visual Studio</span></span>  
  
1.  <span data-ttu-id="24c2d-105">Na barra de menus, escolha **Projeto**, **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="24c2d-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="24c2d-106">A caixa de diálogo **Gerenciador de Referências** é exibida.</span><span class="sxs-lookup"><span data-stu-id="24c2d-106">The **Reference Manager** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="24c2d-107">Na área de **Assemblies**, escolha**Framework** se ele ainda não estiver escolhido.</span><span class="sxs-lookup"><span data-stu-id="24c2d-107">In the **Assemblies** area, choose**Framework** if it isn’t already chosen.</span></span>  
  
3.  <span data-ttu-id="24c2d-108">Na lista de nomes, marque a caixa de seleção **Microsoft.VisualBasic** e, em seguida, escolha o botão **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="24c2d-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24c2d-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="24c2d-109">Example</span></span>  
 <span data-ttu-id="24c2d-110">O código a seguir copia o diretório que `sourcePath` especifica, para o diretório que `destinationPath` especifica.</span><span class="sxs-lookup"><span data-stu-id="24c2d-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="24c2d-111">Esse código também fornece uma caixa de diálogo padrão que mostra a quantidade estimada de tempo que resta antes da conclusão da operação.</span><span class="sxs-lookup"><span data-stu-id="24c2d-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="24c2d-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24c2d-112">See Also</span></span>  
 [<span data-ttu-id="24c2d-113">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="24c2d-113">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
