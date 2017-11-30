---
title: Como escolher pastas com o componente FolderBrowserDialog dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- directories [Windows Forms], choosing
- FolderBrowserDialog component [Windows Forms], choosing directories
- folders [Windows Forms], selecting
- folders [Windows Forms], choosing
- directories [Windows Forms], selecting
ms.assetid: 4593670e-7c7d-4661-b46b-4ffb63258adb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0824fb70fa67628326af38ff7fb5e6c097a0378c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a><span data-ttu-id="19b95-102">Como escolher pastas com o componente FolderBrowserDialog dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="19b95-102">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>
<span data-ttu-id="19b95-103">Muitas vezes, dentro de aplicativos do Windows que você criou, será necessário solicitar que os usuários selecionem uma pasta e com mais frequência que eles salvem um conjunto de arquivos.</span><span class="sxs-lookup"><span data-stu-id="19b95-103">Often, within Windows applications you create, you will have to prompt users to select a folder, most frequently to save a set of files.</span></span> <span data-ttu-id="19b95-104">Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> componente permite que você facilmente realizar essa tarefa.</span><span class="sxs-lookup"><span data-stu-id="19b95-104">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component allows you to easily accomplish this task.</span></span>  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a><span data-ttu-id="19b95-105">Escolher pastas com o componente FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="19b95-105">To choose folders with the FolderBrowserDialog component</span></span>  
  
1.  <span data-ttu-id="19b95-106">Em um procedimento, verifique o <xref:System.Windows.Forms.FolderBrowserDialog> do componente <xref:System.Windows.Forms.Form.DialogResult%2A> propriedade para ver como a caixa de diálogo foi fechada e obter o valor da <xref:System.Windows.Forms.FolderBrowserDialog> do componente <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="19b95-106">In a procedure, check the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.Form.DialogResult%2A> property to see how the dialog box was closed and get the value of the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property.</span></span>  
  
2.  <span data-ttu-id="19b95-107">Se você precisa definir o nível mais alto pasta que será exibido na exibição de árvore da caixa de diálogo, defina o <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> propriedade, que usa um membro do <xref:System.Environment.SpecialFolder> enumeração.</span><span class="sxs-lookup"><span data-stu-id="19b95-107">If you need to set the top-most folder that will appear within the tree view of the dialog box, set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property, which takes a member of the <xref:System.Environment.SpecialFolder> enumeration.</span></span>  
  
3.  <span data-ttu-id="19b95-108">Além disso, você pode definir o <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> propriedade, que especifica o texto da cadeia de caracteres que aparece na parte superior do modo de exibição de árvore do navegador de pasta.</span><span class="sxs-lookup"><span data-stu-id="19b95-108">Additionally, you can set the <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> property, which specifies the text string that appears at the top of the folder-browser tree view.</span></span>  
  
     <span data-ttu-id="19b95-109">No exemplo a seguir, o <xref:System.Windows.Forms.FolderBrowserDialog> componente é usado para selecionar uma pasta, semelhante a quando você cria um projeto no Visual Studio e é solicitado a selecionar uma pasta para salvá-lo no.</span><span class="sxs-lookup"><span data-stu-id="19b95-109">In the example below, the <xref:System.Windows.Forms.FolderBrowserDialog> component is used to select a folder, similar to when you create a project in Visual Studio and are prompted to select a folder to save it in.</span></span> <span data-ttu-id="19b95-110">Neste exemplo, o nome de pasta, em seguida, é exibido em um <xref:System.Windows.Forms.TextBox> controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="19b95-110">In this example, the folder name is then displayed in a <xref:System.Windows.Forms.TextBox> control on the form.</span></span> <span data-ttu-id="19b95-111">É aconselhável colocar o local em uma área editável, como um <xref:System.Windows.Forms.TextBox> controlar, de forma que os usuários podem editar sua seleção no caso de erro ou outros problemas.</span><span class="sxs-lookup"><span data-stu-id="19b95-111">It is a good idea to place the location in an editable area, such as a <xref:System.Windows.Forms.TextBox> control, so that users may edit their selection in case of error or other issues.</span></span> <span data-ttu-id="19b95-112">Este exemplo supõe que um formulário com um <xref:System.Windows.Forms.FolderBrowserDialog> componente e um <xref:System.Windows.Forms.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="19b95-112">This example assumes a form with a <xref:System.Windows.Forms.FolderBrowserDialog> component and a <xref:System.Windows.Forms.TextBox> control.</span></span>  
  
    ```vb  
    Public Sub ChooseFolder()  
        If FolderBrowserDialog1.ShowDialog() = DialogResult.OK Then  
            TextBox1.Text = FolderBrowserDialog1.SelectedPath  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    public void ChooseFolder()  
    {  
        if (folderBrowserDialog1.ShowDialog() == DialogResult.OK)   
        {  
            textBox1.Text = folderBrowserDialog1.SelectedPath;  
        }  
    }  
    ```  
  
    ```cpp  
    public:  
       void ChooseFolder()  
       {  
          if (folderBrowserDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Text = folderBrowserDialog1->SelectedPath;  
          }  
       }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="19b95-113">Para usar essa classe, seu assembly requer um nível de privilégio concedido pelo <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> propriedade, que é parte do <xref:System.Security.Permissions.FileIOPermissionAccess> enumeração.</span><span class="sxs-lookup"><span data-stu-id="19b95-113">To use this class, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> property, which is part of the <xref:System.Security.Permissions.FileIOPermissionAccess> enumeration.</span></span> <span data-ttu-id="19b95-114">Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes.</span><span class="sxs-lookup"><span data-stu-id="19b95-114">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="19b95-115">Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="19b95-115">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="19b95-116">Para obter informações sobre como salvar arquivos, consulte [Como salvar arquivos usando o componente SaveFileDialog](../../../../docs/framework/winforms/controls/how-to-save-files-using-the-savefiledialog-component.md).</span><span class="sxs-lookup"><span data-stu-id="19b95-116">For information on how to save files, see [How to: Save Files Using the SaveFileDialog Component](../../../../docs/framework/winforms/controls/how-to-save-files-using-the-savefiledialog-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19b95-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19b95-117">See Also</span></span>  
 <xref:System.Windows.Forms.FolderBrowserDialog>  
 [<span data-ttu-id="19b95-118">Visão geral do componente FolderBrowserDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="19b95-118">FolderBrowserDialog Component Overview (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-overview-windows-forms.md)  
 [<span data-ttu-id="19b95-119">Componente FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="19b95-119">FolderBrowserDialog Component</span></span>](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)
