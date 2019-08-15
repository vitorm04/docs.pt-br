---
title: 'Como: Carregar uma imagem usando o designer (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 818bc63b5b3bea6c73804f716a72ba3cd1a62b4c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039687"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="524a9-102">Como: Carregar uma imagem usando o designer (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="524a9-102">How to: Load a Picture Using the Designer (Windows Forms)</span></span>

<span data-ttu-id="524a9-103">Com o controle <xref:System.Windows.Forms.PictureBox> de Windows Forms, você pode carregar e exibir uma imagem em um formulário em tempo de design, <xref:System.Windows.Forms.PictureBox.Image%2A> definindo a propriedade como uma imagem válida.</span><span class="sxs-lookup"><span data-stu-id="524a9-103">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="524a9-104">A tabela a seguir mostra os tipos de arquivo disponíveis.</span><span class="sxs-lookup"><span data-stu-id="524a9-104">The following table shows the acceptable file types.</span></span>

|<span data-ttu-id="524a9-105">Tipo</span><span class="sxs-lookup"><span data-stu-id="524a9-105">Type</span></span>|<span data-ttu-id="524a9-106">Extensão de nome de arquivo</span><span class="sxs-lookup"><span data-stu-id="524a9-106">File name extension</span></span>|
|---|---|
|<span data-ttu-id="524a9-107">Bitmap</span><span class="sxs-lookup"><span data-stu-id="524a9-107">Bitmap</span></span>|<span data-ttu-id="524a9-108">.bmp</span><span class="sxs-lookup"><span data-stu-id="524a9-108">.bmp</span></span>|
|<span data-ttu-id="524a9-109">Ícone</span><span class="sxs-lookup"><span data-stu-id="524a9-109">Icon</span></span>|<span data-ttu-id="524a9-110">.ico</span><span class="sxs-lookup"><span data-stu-id="524a9-110">.ico</span></span>|
|<span data-ttu-id="524a9-111">GIF</span><span class="sxs-lookup"><span data-stu-id="524a9-111">GIF</span></span>|<span data-ttu-id="524a9-112">.gif</span><span class="sxs-lookup"><span data-stu-id="524a9-112">.gif</span></span>|
|<span data-ttu-id="524a9-113">Metarquivo</span><span class="sxs-lookup"><span data-stu-id="524a9-113">Metafile</span></span>|<span data-ttu-id="524a9-114">.wmf</span><span class="sxs-lookup"><span data-stu-id="524a9-114">.wmf</span></span>|
|<span data-ttu-id="524a9-115">JPEG</span><span class="sxs-lookup"><span data-stu-id="524a9-115">JPEG</span></span>|<span data-ttu-id="524a9-116">.jpg</span><span class="sxs-lookup"><span data-stu-id="524a9-116">.jpg</span></span>|

## <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="524a9-117">Para exibir uma imagem em tempo de design</span><span class="sxs-lookup"><span data-stu-id="524a9-117">To display a picture at design time</span></span>

1. <span data-ttu-id="524a9-118">Desenhe um <xref:System.Windows.Forms.PictureBox> controle em um formulário.</span><span class="sxs-lookup"><span data-stu-id="524a9-118">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>

2. <span data-ttu-id="524a9-119">Na janela **Propriedades** , selecione a <xref:System.Windows.Forms.PictureBox.Image%2A> Propriedade e, em seguida, selecione o botão de reticências para exibir a caixa de diálogo **abrir** .</span><span class="sxs-lookup"><span data-stu-id="524a9-119">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then select the ellipsis button to display the **Open** dialog box.</span></span>

3. <span data-ttu-id="524a9-120">Se você estiver procurando um tipo de arquivo específico (por exemplo, arquivos. gif), selecione-o na caixa **arquivos do tipo** .</span><span class="sxs-lookup"><span data-stu-id="524a9-120">If you're looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>

4. <span data-ttu-id="524a9-121">Selecione o arquivo que você deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="524a9-121">Select the file you want to display.</span></span>

## <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="524a9-122">Para limpar a imagem em tempo de design</span><span class="sxs-lookup"><span data-stu-id="524a9-122">To clear the picture at design time</span></span>

1. <span data-ttu-id="524a9-123">Na janela **Propriedades** , selecione a <xref:System.Windows.Forms.PictureBox.Image%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="524a9-123">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property.</span></span> <span data-ttu-id="524a9-124">Clique com o botão direito do mouse na pequena imagem em miniatura que aparece à esquerda do nome do objeto de imagem e escolha **Redefinir**.</span><span class="sxs-lookup"><span data-stu-id="524a9-124">Right-click the small thumbnail image that appears to the left of the name of the image object, and then choose **Reset**.</span></span>

## <a name="see-also"></a><span data-ttu-id="524a9-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="524a9-125">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="524a9-126">Visão geral do controle PictureBox</span><span class="sxs-lookup"><span data-stu-id="524a9-126">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="524a9-127">Como: Modificar o tamanho ou o posicionamento de uma imagem em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="524a9-127">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="524a9-128">Como: Definir imagens em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="524a9-128">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="524a9-129">Controle PictureBox</span><span class="sxs-lookup"><span data-stu-id="524a9-129">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
