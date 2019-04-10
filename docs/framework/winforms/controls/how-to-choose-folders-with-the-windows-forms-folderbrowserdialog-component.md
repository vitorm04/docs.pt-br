---
title: 'Como: Escolher pastas com o componente FolderBrowserDialog do Windows Forms'
ms.date: 03/30/2017
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
ms.openlocfilehash: 050af6d10faec3dd09998349dcf96e96ea0f9201
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306177"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a><span data-ttu-id="3c6bb-102">Como: Escolher pastas com o componente FolderBrowserDialog do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3c6bb-102">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>
<span data-ttu-id="3c6bb-103">Muitas vezes, dentro de aplicativos do Windows que você criou, será necessário solicitar que os usuários selecionem uma pasta e com mais frequência que eles salvem um conjunto de arquivos.</span><span class="sxs-lookup"><span data-stu-id="3c6bb-103">Often, within Windows applications you create, you will have to prompt users to select a folder, most frequently to save a set of files.</span></span> <span data-ttu-id="3c6bb-104">Os formulários do Windows <xref:System.Windows.Forms.FolderBrowserDialog> componente permite que você facilmente realizar essa tarefa.</span><span class="sxs-lookup"><span data-stu-id="3c6bb-104">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component allows you to easily accomplish this task.</span></span>  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a><span data-ttu-id="3c6bb-105">Escolher pastas com o componente FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="3c6bb-105">To choose folders with the FolderBrowserDialog component</span></span>  
  
1. <span data-ttu-id="3c6bb-106">Em um procedimento, verifique as <xref:System.Windows.Forms.FolderBrowserDialog> do componente <xref:System.Windows.Forms.Form.DialogResult%2A> propriedade para ver como a caixa de diálogo foi fechada e obter o valor da <xref:System.Windows.Forms.FolderBrowserDialog> do componente <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="3c6bb-106">In a procedure, check the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.Form.DialogResult%2A> property to see how the dialog box was closed and get the value of the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property.</span></span>  
  
2. <span data-ttu-id="3c6bb-107">Se você precisar de pasta de conjunto o mais alto que será exibido dentro da exibição de árvore da caixa de diálogo, defina as <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> propriedade, que usa um membro do <xref:System.Environment.SpecialFolder> enumeração.</span><span class="sxs-lookup"><span data-stu-id="3c6bb-107">If you need to set the top-most folder that will appear within the tree view of the dialog box, set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property, which takes a member of the <xref:System.Environment.SpecialFolder> enumeration.</span></span>  
  
3. <span data-ttu-id="3c6bb-108">Além disso, você pode definir o <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> propriedade, que especifica o texto da cadeia de caracteres que aparece na parte superior do modo de exibição de árvore do navegador de pasta.</span><span class="sxs-lookup"><span data-stu-id="3c6bb-108">Additionally, you can set the <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> property, which specifies the text string that appears at the top of the folder-browser tree view.</span></span>  
  
     <span data-ttu-id="3c6bb-109">No exemplo a seguir, o <xref:System.Windows.Forms.FolderBrowserDialog> componente é usado para selecionar uma pasta, semelhante a quando você cria um projeto no Visual Studio e será solicitado a selecionar uma pasta para salvá-lo no.</span><span class="sxs-lookup"><span data-stu-id="3c6bb-109">In the example below, the <xref:System.Windows.Forms.FolderBrowserDialog> component is used to select a folder, similar to when you create a project in Visual Studio and are prompted to select a folder to save it in.</span></span> <span data-ttu-id="3c6bb-110">Neste exemplo, o nome da pasta é exibido em um <xref:System.Windows.Forms.TextBox> controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="3c6bb-110">In this example, the folder name is then displayed in a <xref:System.Windows.Forms.TextBox> control on the form.</span></span> <span data-ttu-id="3c6bb-111">É uma boa ideia colocar o local em uma área editável, como um <xref:System.Windows.Forms.TextBox> controle, para que os usuários podem editar a seleção em caso de erro ou outros problemas.</span><span class="sxs-lookup"><span data-stu-id="3c6bb-111">It is a good idea to place the location in an editable area, such as a <xref:System.Windows.Forms.TextBox> control, so that users may edit their selection in case of error or other issues.</span></span> <span data-ttu-id="3c6bb-112">Este exemplo pressupõe um formulário com um <xref:System.Windows.Forms.FolderBrowserDialog> componente e um <xref:System.Windows.Forms.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="3c6bb-112">This example assumes a form with a <xref:System.Windows.Forms.FolderBrowserDialog> component and a <xref:System.Windows.Forms.TextBox> control.</span></span>  
  
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
    >  <span data-ttu-id="3c6bb-113">Para usar essa classe, seu assembly requer um nível de privilégio concedido pela <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> propriedade, que é parte do <xref:System.Security.Permissions.FileIOPermissionAccess> enumeração.</span><span class="sxs-lookup"><span data-stu-id="3c6bb-113">To use this class, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> property, which is part of the <xref:System.Security.Permissions.FileIOPermissionAccess> enumeration.</span></span> <span data-ttu-id="3c6bb-114">Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes.</span><span class="sxs-lookup"><span data-stu-id="3c6bb-114">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="3c6bb-115">Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="3c6bb-115">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="3c6bb-116">Para obter informações sobre como salvar arquivos, consulte [como: Salvar arquivos usando o componente SaveFileDialog](how-to-save-files-using-the-savefiledialog-component.md).</span><span class="sxs-lookup"><span data-stu-id="3c6bb-116">For information on how to save files, see [How to: Save Files Using the SaveFileDialog Component](how-to-save-files-using-the-savefiledialog-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c6bb-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c6bb-117">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="3c6bb-118">Visão geral do componente FolderBrowserDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="3c6bb-118">FolderBrowserDialog Component Overview (Windows Forms)</span></span>](folderbrowserdialog-component-overview-windows-forms.md)
- [<span data-ttu-id="3c6bb-119">Componente FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="3c6bb-119">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
