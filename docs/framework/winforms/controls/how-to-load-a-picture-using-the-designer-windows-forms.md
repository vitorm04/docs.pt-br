---
title: Como carregar uma imagem usando o designer (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1dec3c71c0c93ce580925744fe55f05cd2e5f383
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="4621e-102">Como carregar uma imagem usando o designer (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="4621e-102">How to: Load a Picture Using the Designer (Windows Forms)</span></span>
<span data-ttu-id="4621e-103">Com o Windows Forms <xref:System.Windows.Forms.PictureBox> controle, você pode carregar e exibir uma imagem em um formulário em tempo de design, definindo a <xref:System.Windows.Forms.PictureBox.Image%2A> propriedade para uma imagem válida.</span><span class="sxs-lookup"><span data-stu-id="4621e-103">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="4621e-104">A tabela a seguir mostra os tipos de arquivo disponíveis.</span><span class="sxs-lookup"><span data-stu-id="4621e-104">The following table shows the acceptable file types.</span></span>  
  
|<span data-ttu-id="4621e-105">Tipo</span><span class="sxs-lookup"><span data-stu-id="4621e-105">Type</span></span>|<span data-ttu-id="4621e-106">Extensão de nome de arquivo</span><span class="sxs-lookup"><span data-stu-id="4621e-106">File name extension</span></span>|  
|----------|-------------------------|  
|<span data-ttu-id="4621e-107">Bitmap</span><span class="sxs-lookup"><span data-stu-id="4621e-107">Bitmap</span></span>|<span data-ttu-id="4621e-108">.bmp</span><span class="sxs-lookup"><span data-stu-id="4621e-108">.bmp</span></span>|  
|<span data-ttu-id="4621e-109">Ícone</span><span class="sxs-lookup"><span data-stu-id="4621e-109">Icon</span></span>|<span data-ttu-id="4621e-110">.ico</span><span class="sxs-lookup"><span data-stu-id="4621e-110">.ico</span></span>|  
|<span data-ttu-id="4621e-111">GIF</span><span class="sxs-lookup"><span data-stu-id="4621e-111">GIF</span></span>|<span data-ttu-id="4621e-112">.gif</span><span class="sxs-lookup"><span data-stu-id="4621e-112">.gif</span></span>|  
|<span data-ttu-id="4621e-113">Metarquivo</span><span class="sxs-lookup"><span data-stu-id="4621e-113">Metafile</span></span>|<span data-ttu-id="4621e-114">.wmf</span><span class="sxs-lookup"><span data-stu-id="4621e-114">.wmf</span></span>|  
|<span data-ttu-id="4621e-115">JPEG</span><span class="sxs-lookup"><span data-stu-id="4621e-115">JPEG</span></span>|<span data-ttu-id="4621e-116">.jpg</span><span class="sxs-lookup"><span data-stu-id="4621e-116">.jpg</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="4621e-117">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="4621e-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="4621e-118">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="4621e-118">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="4621e-119">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="4621e-119">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="4621e-120">Para exibir uma imagem em tempo de design</span><span class="sxs-lookup"><span data-stu-id="4621e-120">To display a picture at design time</span></span>  
  
1.  <span data-ttu-id="4621e-121">Desenhar um <xref:System.Windows.Forms.PictureBox> controle em um formulário.</span><span class="sxs-lookup"><span data-stu-id="4621e-121">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="4621e-122">Na janela Propriedades, selecione o <xref:System.Windows.Forms.PictureBox.Image%2A> propriedade e, em seguida, clique no botão de reticências para exibir o **abrir** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="4621e-122">On the Properties window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then click the ellipsis button to display the **Open** dialog box.</span></span>  
  
3.  <span data-ttu-id="4621e-123">Se você estiver procurando por um tipo de arquivo específico (por exemplo, arquivos .gif), selecione-o na caixa **Arquivos do tipo**.</span><span class="sxs-lookup"><span data-stu-id="4621e-123">If you are looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>  
  
4.  <span data-ttu-id="4621e-124">Selecione o arquivo que você deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="4621e-124">Select the file you want to display.</span></span>  
  
### <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="4621e-125">Para limpar a imagem em tempo de design</span><span class="sxs-lookup"><span data-stu-id="4621e-125">To clear the picture at design time</span></span>  
  
1.  <span data-ttu-id="4621e-126">Sobre o **propriedades** janela, selecione o <xref:System.Windows.Forms.PictureBox.Image%2A> propriedade e o botão direito do mouse na imagem em miniatura pequena que aparece à esquerda do nome do objeto image.</span><span class="sxs-lookup"><span data-stu-id="4621e-126">On the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property and right-click the small thumbnail image that appears to the left of the name of the image object.</span></span> <span data-ttu-id="4621e-127">Escolha **Redefinir**.</span><span class="sxs-lookup"><span data-stu-id="4621e-127">Choose **Reset**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4621e-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4621e-128">See Also</span></span>  
 <xref:System.Windows.Forms.PictureBox>  
 [<span data-ttu-id="4621e-129">Visão geral do controle PictureBox</span><span class="sxs-lookup"><span data-stu-id="4621e-129">PictureBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [<span data-ttu-id="4621e-130">Como modificar o tamanho ou o posicionamento de uma imagem em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="4621e-130">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)  
 [<span data-ttu-id="4621e-131">Como definir imagens em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="4621e-131">How to: Set Pictures at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [<span data-ttu-id="4621e-132">Controle PictureBox</span><span class="sxs-lookup"><span data-stu-id="4621e-132">PictureBox Control</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
