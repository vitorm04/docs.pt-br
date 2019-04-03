---
title: 'Passo a passo: criar um aplicativo baseado no Windows acessível'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: 19ff49cfa465cce479a4fd5264c565cbb305c84f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823461"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a><span data-ttu-id="f0829-102">Passo a passo: criar um aplicativo baseado no Windows acessível</span><span class="sxs-lookup"><span data-stu-id="f0829-102">Walkthrough: Creating an Accessible Windows-based Application</span></span>
<span data-ttu-id="f0829-103">A criação de um aplicativo acessível tem implicações importantes nos negócios.</span><span class="sxs-lookup"><span data-stu-id="f0829-103">Creating an accessible application has important business implications.</span></span> <span data-ttu-id="f0829-104">Muitos órgãos governamentais tem regulamentos de acessibilidade para a compra de software.</span><span class="sxs-lookup"><span data-stu-id="f0829-104">Many governments have accessibility regulations for software purchase.</span></span> <span data-ttu-id="f0829-105">O logotipo Certified for Windows inclui requisitos de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="f0829-105">The Certified for Windows logo includes accessibility requirements.</span></span> <span data-ttu-id="f0829-106">Estima-se que 30 milhões de moradores, apenas dos EUA, muitos deles clientes potenciais, são afetados pela acessibilidade do software.</span><span class="sxs-lookup"><span data-stu-id="f0829-106">An estimated 30 million residents of the U.S. alone, many of them potential customers, are affected by the accessibility of software.</span></span>  
  
 <span data-ttu-id="f0829-107">Este passo a passo abordará os cinco requisitos de acessibilidade para o logotipo Certified for Windows.</span><span class="sxs-lookup"><span data-stu-id="f0829-107">This walkthrough will address the five accessibility requirements for the Certified for Windows logo.</span></span> <span data-ttu-id="f0829-108">De acordo com a esses requisitos, um aplicativo acessível:</span><span class="sxs-lookup"><span data-stu-id="f0829-108">According to these requirements, an accessible application will:</span></span>  
  
-   <span data-ttu-id="f0829-109">Dará suporte às configurações de tamanho, cor, fonte e de entrada do Painel de Controle.</span><span class="sxs-lookup"><span data-stu-id="f0829-109">Support Control Panel size, color, font, and input settings.</span></span> <span data-ttu-id="f0829-110">A barra de menus, a barra de título, as bordas e a barra de status serão todas redimensionadas quando o usuário alterar as configurações do painel de controle.</span><span class="sxs-lookup"><span data-stu-id="f0829-110">The menu bar, title bar, borders, and status bar will all resize themselves when the user changes the control panel settings.</span></span> <span data-ttu-id="f0829-111">Nenhuma alteração adicional aos controles ou ao código será necessária neste aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0829-111">No additional changes to the controls or code are required in this application.</span></span>  
  
-   <span data-ttu-id="f0829-112">Dará suporte ao modo de alto contraste.</span><span class="sxs-lookup"><span data-stu-id="f0829-112">Support High Contrast mode.</span></span>  
  
-   <span data-ttu-id="f0829-113">Fornecerá acesso ao teclado documentado a todos os recursos.</span><span class="sxs-lookup"><span data-stu-id="f0829-113">Provide documented keyboard access to all features.</span></span>  
  
-   <span data-ttu-id="f0829-114">Exporá o local do foco do teclado visualmente e programaticamente.</span><span class="sxs-lookup"><span data-stu-id="f0829-114">Expose location of the keyboard focus visually and programmatically.</span></span>  
  
-   <span data-ttu-id="f0829-115">Evitará a transmissão de informações importantes apenas através do som.</span><span class="sxs-lookup"><span data-stu-id="f0829-115">Avoid conveying important information by sound alone.</span></span>  
  
 <span data-ttu-id="f0829-116">Para obter mais informações, consulte [Recursos para projetar aplicativos acessíveis](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span><span class="sxs-lookup"><span data-stu-id="f0829-116">For more information, see [Resources for Designing Accessible Applications](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span></span>  
  
 <span data-ttu-id="f0829-117">Para obter informações sobre suporte a diferentes layouts de teclado, consulte [Melhores práticas para o desenvolvimento de aplicativos prontos para o mundo](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span><span class="sxs-lookup"><span data-stu-id="f0829-117">For information on supporting varying keyboard layouts, see [Best Practices for Developing World-Ready Applications](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="f0829-118">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="f0829-118">Creating the Project</span></span>  
 <span data-ttu-id="f0829-119">Este passo a passo cria a interface do usuário para um aplicativo que recebe pedidos de pizza.</span><span class="sxs-lookup"><span data-stu-id="f0829-119">This walkthrough creates the user interface for an application that takes pizza orders.</span></span> <span data-ttu-id="f0829-120">Ele consiste em uma <xref:System.Windows.Forms.TextBox> para o nome do cliente, uma <xref:System.Windows.Forms.RadioButton> grupo para selecionar o tamanho da pizza, um <xref:System.Windows.Forms.CheckedListBox> para selecionar os ingredientes, dois controles de botão rotulado como ordem e Cancelar e um Menu com um comando Sair.</span><span class="sxs-lookup"><span data-stu-id="f0829-120">It consists of a <xref:System.Windows.Forms.TextBox> for the customer's name, a <xref:System.Windows.Forms.RadioButton> group to select the pizza size, a <xref:System.Windows.Forms.CheckedListBox> for selecting the toppings, two Button controls labeled Order and Cancel, and a Menu with an Exit command.</span></span>  
  
 <span data-ttu-id="f0829-121">O usuário insere o nome do cliente, o tamanho da pizza e os ingredientes desejados.</span><span class="sxs-lookup"><span data-stu-id="f0829-121">The user enters the customer's name, the size of the pizza, and the toppings desired.</span></span> <span data-ttu-id="f0829-122">Quando o usuário clica no botão Pedir, um resumo do pedido e o custo são exibidos em uma caixa de mensagem e os controles são limpos e preparados para o próximo pedido.</span><span class="sxs-lookup"><span data-stu-id="f0829-122">When the user clicks the Order button, a summary of the order and its cost are displayed in a message box and the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="f0829-123">Quando o usuário clica no botão Cancelar, os controles são limpos e preparados para o próximo pedido.</span><span class="sxs-lookup"><span data-stu-id="f0829-123">When the user clicks the Cancel button, the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="f0829-124">Quando o usuário clica no item de menu Sair, o programa é fechado.</span><span class="sxs-lookup"><span data-stu-id="f0829-124">When the user clicks the Exit menu item, the program closes.</span></span>  
  
 <span data-ttu-id="f0829-125">A ênfase deste passo a passo não é no código para um sistema de pedidos de vendas, mas na acessibilidade da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="f0829-125">The emphasis of this walkthrough is not the code for a retail order system, but the accessibility of the user interface.</span></span> <span data-ttu-id="f0829-126">O passo a passo demonstra os recursos de acessibilidade de vários controles usados com frequência, incluindo botões, botões de opção, caixas de texto e rótulos.</span><span class="sxs-lookup"><span data-stu-id="f0829-126">The walkthrough demonstrates the accessibility features of several frequently used controls, including buttons, radio buttons, text boxes, and labels.</span></span>  
  
#### <a name="to-begin-making-the-application"></a><span data-ttu-id="f0829-127">Para começar a criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="f0829-127">To begin making the application</span></span>  
  
-   <span data-ttu-id="f0829-128">Criar um novo aplicativo do Windows no Visual Basic ou Visual C#.</span><span class="sxs-lookup"><span data-stu-id="f0829-128">Create a new Windows Application in Visual Basic or Visual C#.</span></span> <span data-ttu-id="f0829-129">Nomeie o projeto como **PizzaOrder**.</span><span class="sxs-lookup"><span data-stu-id="f0829-129">Name the project **PizzaOrder**.</span></span> <span data-ttu-id="f0829-130">(Para obter detalhes, consulte [Criando novas soluções e projetos](/visualstudio/ide/creating-solutions-and-projects)).</span><span class="sxs-lookup"><span data-stu-id="f0829-130">(For details see [Creating New Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).)</span></span>  
  
## <a name="adding-the-controls-to-the-form"></a><span data-ttu-id="f0829-131">Adicionando os controles ao formulário</span><span class="sxs-lookup"><span data-stu-id="f0829-131">Adding the Controls to the Form</span></span>  
 <span data-ttu-id="f0829-132">Ao adicionar controles a um formulário, tenha em mente as seguintes diretrizes para criar um aplicativo acessível:</span><span class="sxs-lookup"><span data-stu-id="f0829-132">When adding the controls to a form, keep in mind the following guidelines to make an accessible application:</span></span>  
  
-   <span data-ttu-id="f0829-133">Defina as <xref:System.Windows.Forms.Control.AccessibleDescription%2A> e <xref:System.Windows.Forms.Control.AccessibleName%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="f0829-133">Set the <xref:System.Windows.Forms.Control.AccessibleDescription%2A> and <xref:System.Windows.Forms.Control.AccessibleName%2A> properties.</span></span> <span data-ttu-id="f0829-134">Neste exemplo, a configuração padrão para o <xref:System.Windows.Forms.Control.AccessibleRole%2A> é suficiente.</span><span class="sxs-lookup"><span data-stu-id="f0829-134">In this example, the Default setting for the <xref:System.Windows.Forms.Control.AccessibleRole%2A> is sufficient.</span></span> <span data-ttu-id="f0829-135">Para obter mais informações sobre as propriedades de acessibilidade, consulte [Fornecendo informações de acessibilidade para controles em um Windows Form](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="f0829-135">For more information on the accessibility properties, see [Providing Accessibility Information for Controls on a Windows Form](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span></span>  
  
-   <span data-ttu-id="f0829-136">Defina o tamanho da fonte como 10 pontos ou mais.</span><span class="sxs-lookup"><span data-stu-id="f0829-136">Set the font size to 10 points or larger.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f0829-137">Se você definir o tamanho da fonte do formulário como 10 ao iniciar, todos os controles adicionados posteriormente ao formulário terão um tamanho da fonte de 10.</span><span class="sxs-lookup"><span data-stu-id="f0829-137">If you set the font size of the form to 10 when you start, then all controls subsequently added to the form will have a font size of 10.</span></span>  
  
-   <span data-ttu-id="f0829-138">Certifique-se de que qualquer controle de rótulo que descreve um controle TextBox venha logo antes do controle TextBox na ordem de tabulação.</span><span class="sxs-lookup"><span data-stu-id="f0829-138">Make sure any Label control that describes a TextBox control immediately precedes the TextBox control in the tab order.</span></span>  
  
-   <span data-ttu-id="f0829-139">Adicione uma chave de acesso, usando o caractere "&", para o <xref:System.Windows.Forms.Control.Text%2A> propriedade de qualquer controle que o usuário deseja navegar.</span><span class="sxs-lookup"><span data-stu-id="f0829-139">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of any control the user may want to navigate to.</span></span>  
  
-   <span data-ttu-id="f0829-140">Adicione uma chave de acesso, usando o caractere "&", para o <xref:System.Windows.Forms.Control.Text%2A> propriedade do rótulo que precede um controle que o usuário poderá navegar para.</span><span class="sxs-lookup"><span data-stu-id="f0829-140">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of the label that precedes a control that the user may want to navigate to.</span></span> <span data-ttu-id="f0829-141">Definir rótulos <xref:System.Windows.Forms.Label.UseMnemonic%2A> propriedade para `true`, de modo que o foco é definido para o próximo controle na ordem de tabulação quando o usuário pressiona a tecla de acesso.</span><span class="sxs-lookup"><span data-stu-id="f0829-141">Set the labels' <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`, so that the focus is set to the next control in the tab order when the user presses the access key.</span></span>  
  
-   <span data-ttu-id="f0829-142">Adicione chaves de acesso a todos os itens de menu.</span><span class="sxs-lookup"><span data-stu-id="f0829-142">Add access keys to all menu items.</span></span>  
  
#### <a name="to-make-your-windows-application-accessible"></a><span data-ttu-id="f0829-143">Para tornar seu aplicativo do Windows acessível</span><span class="sxs-lookup"><span data-stu-id="f0829-143">To make your Windows Application accessible</span></span>  
  
-   <span data-ttu-id="f0829-144">Adicione os controles ao formulário e defina as propriedades conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="f0829-144">Add the controls to the form and set the properties as described below.</span></span> <span data-ttu-id="f0829-145">Veja a imagem no final da tabela para um modelo de como organizar os controles no formulário.</span><span class="sxs-lookup"><span data-stu-id="f0829-145">See the picture at the end of the table for a model of how to arrange the controls on the form.</span></span>  
  
    |<span data-ttu-id="f0829-146">Objeto</span><span class="sxs-lookup"><span data-stu-id="f0829-146">Object</span></span>|<span data-ttu-id="f0829-147">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f0829-147">Property</span></span>|<span data-ttu-id="f0829-148">Valor</span><span class="sxs-lookup"><span data-stu-id="f0829-148">Value</span></span>|  
    |------------|--------------|-----------|  
    |<span data-ttu-id="f0829-149">Form1</span><span class="sxs-lookup"><span data-stu-id="f0829-149">Form1</span></span>|<span data-ttu-id="f0829-150">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="f0829-150">AccessibleDescription</span></span>|<span data-ttu-id="f0829-151">Formulário de pedido</span><span class="sxs-lookup"><span data-stu-id="f0829-151">Order form</span></span>|  
    ||<span data-ttu-id="f0829-152">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="f0829-152">AccessibleName</span></span>|<span data-ttu-id="f0829-153">Formulário de pedido</span><span class="sxs-lookup"><span data-stu-id="f0829-153">Order form</span></span>|  
    ||<span data-ttu-id="f0829-154">Tamanho da fonte</span><span class="sxs-lookup"><span data-stu-id="f0829-154">Font Size</span></span>|<span data-ttu-id="f0829-155">10</span><span class="sxs-lookup"><span data-stu-id="f0829-155">10</span></span>|  
    ||<span data-ttu-id="f0829-156">Texto</span><span class="sxs-lookup"><span data-stu-id="f0829-156">Text</span></span>|<span data-ttu-id="f0829-157">Formulário de pedido de pizza</span><span class="sxs-lookup"><span data-stu-id="f0829-157">Pizza Order Form</span></span>|  
    |<span data-ttu-id="f0829-158">PictureBox</span><span class="sxs-lookup"><span data-stu-id="f0829-158">PictureBox</span></span>|<span data-ttu-id="f0829-159">Nome</span><span class="sxs-lookup"><span data-stu-id="f0829-159">Name</span></span>|<span data-ttu-id="f0829-160">logotipo</span><span class="sxs-lookup"><span data-stu-id="f0829-160">logo</span></span>|  
    ||<span data-ttu-id="f0829-161">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="f0829-161">AccessibleDescription</span></span>|<span data-ttu-id="f0829-162">Uma fatia de pizza</span><span class="sxs-lookup"><span data-stu-id="f0829-162">A slice of pizza</span></span>|  
    ||<span data-ttu-id="f0829-163">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="f0829-163">AccessibleName</span></span>|<span data-ttu-id="f0829-164">Logotipo da empresa</span><span class="sxs-lookup"><span data-stu-id="f0829-164">Company logo</span></span>|  
    ||<span data-ttu-id="f0829-165">Image</span><span class="sxs-lookup"><span data-stu-id="f0829-165">Image</span></span>|<span data-ttu-id="f0829-166">Qualquer ícone ou bitmap</span><span class="sxs-lookup"><span data-stu-id="f0829-166">Any icon or bitmap</span></span>|  
    |<span data-ttu-id="f0829-167">Rotular</span><span class="sxs-lookup"><span data-stu-id="f0829-167">Label</span></span>|<span data-ttu-id="f0829-168">Nome</span><span class="sxs-lookup"><span data-stu-id="f0829-168">Name</span></span>|<span data-ttu-id="f0829-169">companyLabel</span><span class="sxs-lookup"><span data-stu-id="f0829-169">companyLabel</span></span>|  
    ||<span data-ttu-id="f0829-170">Texto</span><span class="sxs-lookup"><span data-stu-id="f0829-170">Text</span></span>|<span data-ttu-id="f0829-171">Pizza boa</span><span class="sxs-lookup"><span data-stu-id="f0829-171">Good Pizza</span></span>|  
    ||<span data-ttu-id="f0829-172">TabIndex</span><span class="sxs-lookup"><span data-stu-id="f0829-172">TabIndex</span></span>|<span data-ttu-id="f0829-173">1</span><span class="sxs-lookup"><span data-stu-id="f0829-173">1</span></span>|  
    ||<span data-ttu-id="f0829-174">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="f0829-174">AccessibleDescription</span></span>|<span data-ttu-id="f0829-175">Nome da empresa</span><span class="sxs-lookup"><span data-stu-id="f0829-175">Company name</span></span>|  
    ||<span data-ttu-id="f0829-176">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="f0829-176">AccessibleName</span></span>|<span data-ttu-id="f0829-177">Nome da empresa</span><span class="sxs-lookup"><span data-stu-id="f0829-177">Company name</span></span>|  
    ||<span data-ttu-id="f0829-178">Backcolor</span><span class="sxs-lookup"><span data-stu-id="f0829-178">Backcolor</span></span>|<span data-ttu-id="f0829-179">Azul</span><span class="sxs-lookup"><span data-stu-id="f0829-179">Blue</span></span>|  
    ||<span data-ttu-id="f0829-180">Forecolor</span><span class="sxs-lookup"><span data-stu-id="f0829-180">Forecolor</span></span>|<span data-ttu-id="f0829-181">Amarelo</span><span class="sxs-lookup"><span data-stu-id="f0829-181">Yellow</span></span>|  
    ||<span data-ttu-id="f0829-182">Tamanho da fonte</span><span class="sxs-lookup"><span data-stu-id="f0829-182">Font size</span></span>|<span data-ttu-id="f0829-183">18</span><span class="sxs-lookup"><span data-stu-id="f0829-183">18</span></span>|  
    |<span data-ttu-id="f0829-184">Rotular</span><span class="sxs-lookup"><span data-stu-id="f0829-184">Label</span></span>|<span data-ttu-id="f0829-185">Nome</span><span class="sxs-lookup"><span data-stu-id="f0829-185">Name</span></span>|<span data-ttu-id="f0829-186">customerLabel</span><span class="sxs-lookup"><span data-stu-id="f0829-186">customerLabel</span></span>|  
    ||<span data-ttu-id="f0829-187">Texto</span><span class="sxs-lookup"><span data-stu-id="f0829-187">Text</span></span>|<span data-ttu-id="f0829-188">&Nome</span><span class="sxs-lookup"><span data-stu-id="f0829-188">&Name</span></span>|  
    ||<span data-ttu-id="f0829-189">TabIndex</span><span class="sxs-lookup"><span data-stu-id="f0829-189">TabIndex</span></span>|<span data-ttu-id="f0829-190">2</span><span class="sxs-lookup"><span data-stu-id="f0829-190">2</span></span>|  
    ||<span data-ttu-id="f0829-191">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="f0829-191">AccessibleDescription</span></span>|<span data-ttu-id="f0829-192">Rótulo de nome do cliente</span><span class="sxs-lookup"><span data-stu-id="f0829-192">Customer name label</span></span>|  
    ||<span data-ttu-id="f0829-193">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="f0829-193">AccessibleName</span></span>|<span data-ttu-id="f0829-194">Rótulo de nome do cliente</span><span class="sxs-lookup"><span data-stu-id="f0829-194">Customer name label</span></span>|  
    ||<span data-ttu-id="f0829-195">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="f0829-195">UseMnemonic</span></span>|<span data-ttu-id="f0829-196">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="f0829-196">True</span></span>|  
    |<span data-ttu-id="f0829-197">TextBox</span><span class="sxs-lookup"><span data-stu-id="f0829-197">TextBox</span></span>|<span data-ttu-id="f0829-198">Nome</span><span class="sxs-lookup"><span data-stu-id="f0829-198">Name</span></span>|<span data-ttu-id="f0829-199">customerName</span><span class="sxs-lookup"><span data-stu-id="f0829-199">customerName</span></span>|  
    ||<span data-ttu-id="f0829-200">Texto</span><span class="sxs-lookup"><span data-stu-id="f0829-200">Text</span></span>|<span data-ttu-id="f0829-201">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="f0829-201">(none)</span></span>|  
    ||<span data-ttu-id="f0829-202">TabIndex</span><span class="sxs-lookup"><span data-stu-id="f0829-202">TabIndex</span></span>|<span data-ttu-id="f0829-203">3</span><span class="sxs-lookup"><span data-stu-id="f0829-203">3</span></span>|  
    ||<span data-ttu-id="f0829-204">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="f0829-204">AccessibleDescription</span></span>|<span data-ttu-id="f0829-205">Nome do cliente</span><span class="sxs-lookup"><span data-stu-id="f0829-205">Customer name</span></span>|  
    ||<span data-ttu-id="f0829-206">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="f0829-206">AccessibleName</span></span>|<span data-ttu-id="f0829-207">Nome do cliente</span><span class="sxs-lookup"><span data-stu-id="f0829-207">Customer name</span></span>|  
    |<span data-ttu-id="f0829-208">GroupBox</span><span class="sxs-lookup"><span data-stu-id="f0829-208">GroupBox</span></span>|<span data-ttu-id="f0829-209">Nome</span><span class="sxs-lookup"><span data-stu-id="f0829-209">Name</span></span>|<span data-ttu-id="f0829-210">sizeOptions</span><span class="sxs-lookup"><span data-stu-id="f0829-210">sizeOptions</span></span>|  
    ||<span data-ttu-id="f0829-211">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="f0829-211">AccessibleDescription</span></span>|<span data-ttu-id="f0829-212">Opções de tamanho de pizza</span><span class="sxs-lookup"><span data-stu-id="f0829-212">Pizza size options</span></span>|  
    ||<span data-ttu-id="f0829-213">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="f0829-213">AccessibleName</span></span>|<span data-ttu-id="f0829-214">Opções de tamanho de pizza</span><span class="sxs-lookup"><span data-stu-id="f0829-214">Pizza size options</span></span>|  
    ||<span data-ttu-id="f0829-215">Texto</span><span class="sxs-lookup"><span data-stu-id="f0829-215">Text</span></span>|<span data-ttu-id="f0829-216">Tamanho de pizza</span><span class="sxs-lookup"><span data-stu-id="f0829-216">Pizza size</span></span>|  
    ||<span data-ttu-id="f0829-217">TabIndex</span><span class="sxs-lookup"><span data-stu-id="f0829-217">TabIndex</span></span>|<span data-ttu-id="f0829-218">4</span><span class="sxs-lookup"><span data-stu-id="f0829-218">4</span></span>|  
    |<span data-ttu-id="f0829-219">RadioButton</span><span class="sxs-lookup"><span data-stu-id="f0829-219">RadioButton</span></span>|<span data-ttu-id="f0829-220">Nome</span><span class="sxs-lookup"><span data-stu-id="f0829-220">Name</span></span>|<span data-ttu-id="f0829-221">smallPizza</span><span class="sxs-lookup"><span data-stu-id="f0829-221">smallPizza</span></span>|  
    ||<span data-ttu-id="f0829-222">Texto</span><span class="sxs-lookup"><span data-stu-id="f0829-222">Text</span></span>|<span data-ttu-id="f0829-223">&Pequena $6.00</span><span class="sxs-lookup"><span data-stu-id="f0829-223">&Small $6.00</span></span>|  
    ||<span data-ttu-id="f0829-224">Selecionado</span><span class="sxs-lookup"><span data-stu-id="f0829-224">Checked</span></span>|<span data-ttu-id="f0829-225">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="f0829-225">True</span></span>|  
    ||<span data-ttu-id="f0829-226">TabIndex</span><span class="sxs-lookup"><span data-stu-id="f0829-226">TabIndex</span></span>|<span data-ttu-id="f0829-227">0</span><span class="sxs-lookup"><span data-stu-id="f0829-227">0</span></span>|  
    ||<span data-ttu-id="f0829-228">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="f0829-228">AccessibleDescription</span></span>|<span data-ttu-id="f0829-229">Pizza pequena</span><span class="sxs-lookup"><span data-stu-id="f0829-229">Small pizza</span></span>|  
    ||<span data-ttu-id="f0829-230">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="f0829-230">AccessibleName</span></span>|<span data-ttu-id="f0829-231">Pizza pequena</span><span class="sxs-lookup"><span data-stu-id="f0829-231">Small pizza</span></span>|  
    |<span data-ttu-id="f0829-232">RadioButton</span><span class="sxs-lookup"><span data-stu-id="f0829-232">RadioButton</span></span>|<span data-ttu-id="f0829-233">Nome</span><span class="sxs-lookup"><span data-stu-id="f0829-233">Name</span></span>|<span data-ttu-id="f0829-234">largePizza</span><span class="sxs-lookup"><span data-stu-id="f0829-234">largePizza</span></span>|  
    ||<span data-ttu-id="f0829-235">Texto</span><span class="sxs-lookup"><span data-stu-id="f0829-235">Text</span></span>|<span data-ttu-id="f0829-236">&Grande $10.00</span><span class="sxs-lookup"><span data-stu-id="f0829-236">&Large $10.00</span></span>|  
    ||<span data-ttu-id="f0829-237">TabIndex</span><span class="sxs-lookup"><span data-stu-id="f0829-237">TabIndex</span></span>|<span data-ttu-id="f0829-238">1</span><span class="sxs-lookup"><span data-stu-id="f0829-238">1</span></span>|  
    ||<span data-ttu-id="f0829-239">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="f0829-239">AccessibleDescription</span></span>|<span data-ttu-id="f0829-240">Pizza grande</span><span class="sxs-lookup"><span data-stu-id="f0829-240">Large pizza</span></span>|  
    ||<span data-ttu-id="f0829-241">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="f0829-241">AccessibleName</span></span>|<span data-ttu-id="f0829-242">Pizza grande</span><span class="sxs-lookup"><span data-stu-id="f0829-242">Large pizza</span></span>|  
    |<span data-ttu-id="f0829-243">Rotular</span><span class="sxs-lookup"><span data-stu-id="f0829-243">Label</span></span>|<span data-ttu-id="f0829-244">Nome</span><span class="sxs-lookup"><span data-stu-id="f0829-244">Name</span></span>|<span data-ttu-id="f0829-245">toppingsLabel</span><span class="sxs-lookup"><span data-stu-id="f0829-245">toppingsLabel</span></span>|  
    ||<span data-ttu-id="f0829-246">Texto</span><span class="sxs-lookup"><span data-stu-id="f0829-246">Text</span></span>|<span data-ttu-id="f0829-247">&Ingredientes ($0.75 cada)</span><span class="sxs-lookup"><span data-stu-id="f0829-247">&Toppings ($0.75 each)</span></span>|  
    ||<span data-ttu-id="f0829-248">TabIndex</span><span class="sxs-lookup"><span data-stu-id="f0829-248">TabIndex</span></span>|<span data-ttu-id="f0829-249">5</span><span class="sxs-lookup"><span data-stu-id="f0829-249">5</span></span>|  
    ||<span data-ttu-id="f0829-250">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="f0829-250">AccessibleDescription</span></span>|<span data-ttu-id="f0829-251">Rótulo de ingredientes</span><span class="sxs-lookup"><span data-stu-id="f0829-251">Toppings label</span></span>|  
    ||<span data-ttu-id="f0829-252">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="f0829-252">AccessibleName</span></span>|<span data-ttu-id="f0829-253">Rótulo de ingredientes</span><span class="sxs-lookup"><span data-stu-id="f0829-253">Toppings label</span></span>|  
    ||<span data-ttu-id="f0829-254">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="f0829-254">UseMnemonic</span></span>|<span data-ttu-id="f0829-255">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="f0829-255">True</span></span>|  
    |<span data-ttu-id="f0829-256">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="f0829-256">CheckedListBox</span></span>|<span data-ttu-id="f0829-257">Nome</span><span class="sxs-lookup"><span data-stu-id="f0829-257">Name</span></span>|<span data-ttu-id="f0829-258">ingredientes</span><span class="sxs-lookup"><span data-stu-id="f0829-258">toppings</span></span>|  
    ||<span data-ttu-id="f0829-259">TabIndex</span><span class="sxs-lookup"><span data-stu-id="f0829-259">TabIndex</span></span>|<span data-ttu-id="f0829-260">6</span><span class="sxs-lookup"><span data-stu-id="f0829-260">6</span></span>|  
    ||<span data-ttu-id="f0829-261">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="f0829-261">AccessibleDescription</span></span>|<span data-ttu-id="f0829-262">Ingredientes disponíveis</span><span class="sxs-lookup"><span data-stu-id="f0829-262">Available toppings</span></span>|  
    ||<span data-ttu-id="f0829-263">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="f0829-263">AccessibleName</span></span>|<span data-ttu-id="f0829-264">Ingredientes disponíveis</span><span class="sxs-lookup"><span data-stu-id="f0829-264">Available toppings</span></span>|  
    ||<span data-ttu-id="f0829-265">Itens</span><span class="sxs-lookup"><span data-stu-id="f0829-265">Items</span></span>|<span data-ttu-id="f0829-266">Pepperoni, Linguiça, Cogumelos</span><span class="sxs-lookup"><span data-stu-id="f0829-266">Pepperoni, Sausage, Mushrooms</span></span>|  
    |<span data-ttu-id="f0829-267">Botão</span><span class="sxs-lookup"><span data-stu-id="f0829-267">Button</span></span>|<span data-ttu-id="f0829-268">Nome</span><span class="sxs-lookup"><span data-stu-id="f0829-268">Name</span></span>|<span data-ttu-id="f0829-269">ordem</span><span class="sxs-lookup"><span data-stu-id="f0829-269">order</span></span>|  
    ||<span data-ttu-id="f0829-270">Texto</span><span class="sxs-lookup"><span data-stu-id="f0829-270">Text</span></span>|<span data-ttu-id="f0829-271">&Ordem</span><span class="sxs-lookup"><span data-stu-id="f0829-271">&Order</span></span>|  
    ||<span data-ttu-id="f0829-272">TabIndex</span><span class="sxs-lookup"><span data-stu-id="f0829-272">TabIndex</span></span>|<span data-ttu-id="f0829-273">7</span><span class="sxs-lookup"><span data-stu-id="f0829-273">7</span></span>|  
    ||<span data-ttu-id="f0829-274">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="f0829-274">AccessibleDescription</span></span>|<span data-ttu-id="f0829-275">Total do pedido</span><span class="sxs-lookup"><span data-stu-id="f0829-275">Total the order</span></span>|  
    ||<span data-ttu-id="f0829-276">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="f0829-276">AccessibleName</span></span>|<span data-ttu-id="f0829-277">Pedido total</span><span class="sxs-lookup"><span data-stu-id="f0829-277">Total order</span></span>|  
    |<span data-ttu-id="f0829-278">Botão</span><span class="sxs-lookup"><span data-stu-id="f0829-278">Button</span></span>|<span data-ttu-id="f0829-279">Nome</span><span class="sxs-lookup"><span data-stu-id="f0829-279">Name</span></span>|<span data-ttu-id="f0829-280">cancelar</span><span class="sxs-lookup"><span data-stu-id="f0829-280">cancel</span></span>|  
    ||<span data-ttu-id="f0829-281">Texto</span><span class="sxs-lookup"><span data-stu-id="f0829-281">Text</span></span>|<span data-ttu-id="f0829-282">&Cancelar</span><span class="sxs-lookup"><span data-stu-id="f0829-282">&Cancel</span></span>|  
    ||<span data-ttu-id="f0829-283">TabIndex</span><span class="sxs-lookup"><span data-stu-id="f0829-283">TabIndex</span></span>|<span data-ttu-id="f0829-284">8</span><span class="sxs-lookup"><span data-stu-id="f0829-284">8</span></span>|  
    ||<span data-ttu-id="f0829-285">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="f0829-285">AccessibleDescription</span></span>|<span data-ttu-id="f0829-286">Cancelar o pedido</span><span class="sxs-lookup"><span data-stu-id="f0829-286">Cancel the order</span></span>|  
    ||<span data-ttu-id="f0829-287">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="f0829-287">AccessibleName</span></span>|<span data-ttu-id="f0829-288">Cancelar pedido</span><span class="sxs-lookup"><span data-stu-id="f0829-288">Cancel order</span></span>|  
    |<span data-ttu-id="f0829-289">MainMenu</span><span class="sxs-lookup"><span data-stu-id="f0829-289">MainMenu</span></span>|<span data-ttu-id="f0829-290">Nome</span><span class="sxs-lookup"><span data-stu-id="f0829-290">Name</span></span>|<span data-ttu-id="f0829-291">theMainMenu</span><span class="sxs-lookup"><span data-stu-id="f0829-291">theMainMenu</span></span>|  
    |<span data-ttu-id="f0829-292">MenuItem</span><span class="sxs-lookup"><span data-stu-id="f0829-292">MenuItem</span></span>|<span data-ttu-id="f0829-293">Nome</span><span class="sxs-lookup"><span data-stu-id="f0829-293">Name</span></span>|<span data-ttu-id="f0829-294">fileCommands</span><span class="sxs-lookup"><span data-stu-id="f0829-294">fileCommands</span></span>|  
    ||<span data-ttu-id="f0829-295">Texto</span><span class="sxs-lookup"><span data-stu-id="f0829-295">Text</span></span>|<span data-ttu-id="f0829-296">&Arquivo</span><span class="sxs-lookup"><span data-stu-id="f0829-296">&File</span></span>|  
    |<span data-ttu-id="f0829-297">MenuItem</span><span class="sxs-lookup"><span data-stu-id="f0829-297">MenuItem</span></span>|<span data-ttu-id="f0829-298">Nome</span><span class="sxs-lookup"><span data-stu-id="f0829-298">Name</span></span>|<span data-ttu-id="f0829-299">exitApp</span><span class="sxs-lookup"><span data-stu-id="f0829-299">exitApp</span></span>|  
    ||<span data-ttu-id="f0829-300">Texto</span><span class="sxs-lookup"><span data-stu-id="f0829-300">Text</span></span>|<span data-ttu-id="f0829-301">Sa&ir</span><span class="sxs-lookup"><span data-stu-id="f0829-301">E&xit</span></span>|
    
      <span data-ttu-id="f0829-302">Seu formulário será algo parecido com a imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="f0829-302">Your form will look something like the following image:</span></span>
    
      ![O formulário de pedido de pizza com uma seleção de nome de caixa de texto e o tamanho e ingredientes.](./media/walkthrough-creating-an-accessible-windows-based-application/visual-basic-pizza-order-form.gif)  

  
## <a name="supporting-high-contrast-mode"></a><span data-ttu-id="f0829-304">Suporte ao modo de alto contraste</span><span class="sxs-lookup"><span data-stu-id="f0829-304">Supporting High Contrast Mode</span></span>  
 <span data-ttu-id="f0829-305">O modo de Alto Contraste é uma configuração de sistema do Windows que melhora a legibilidade, usando cores contrastantes e tamanhos de fonte que são benéficos para usuários com deficiências visuais.</span><span class="sxs-lookup"><span data-stu-id="f0829-305">High Contrast mode is a Windows system setting that improves readability by using contrasting colors and font sizes that are beneficial for visually impaired users.</span></span> <span data-ttu-id="f0829-306">O <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> é fornecida para determinar se o modo de alto contraste está definido.</span><span class="sxs-lookup"><span data-stu-id="f0829-306">The <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> property is provided to determine whether the High Contrast mode is set.</span></span>  
  
 <span data-ttu-id="f0829-307">Se SystemInformation.HighContrast for `true`, o aplicativo deverá:</span><span class="sxs-lookup"><span data-stu-id="f0829-307">If SystemInformation.HighContrast is `true`, the application should:</span></span>  
  
-   <span data-ttu-id="f0829-308">Exibir todos os elementos de interface do usuário usando o esquema de cores do sistema</span><span class="sxs-lookup"><span data-stu-id="f0829-308">Display all user interface elements using the system color scheme</span></span>  
  
-   <span data-ttu-id="f0829-309">Transmitir, por dicas visuais ou por som, quaisquer informações que são transmitidas por meio de cor.</span><span class="sxs-lookup"><span data-stu-id="f0829-309">Convey by visual cues or sound any information that is conveyed through color.</span></span> <span data-ttu-id="f0829-310">Por exemplo, se determinados itens de lista estão realçados com uma fonte vermelha, você também pode adicionar negrito à fonte para que o usuário tenha uma dica diferente das cores de que os itens estão realçados.</span><span class="sxs-lookup"><span data-stu-id="f0829-310">For example, if particular list items are highlighted by using a red font, you could also add bold to the font, so that the user has a non-color cue that the items are highlighted.</span></span>  
  
-   <span data-ttu-id="f0829-311">Omitir imagens ou padrões por trás do texto</span><span class="sxs-lookup"><span data-stu-id="f0829-311">Omit any images or patterns behind text</span></span>  
  
 <span data-ttu-id="f0829-312">O aplicativo deve verificar a configuração da <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> quando o aplicativo é iniciado e responder ao evento de sistema <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span><span class="sxs-lookup"><span data-stu-id="f0829-312">The application should check the setting of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> when the application starts and respond to the system event <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span></span> <span data-ttu-id="f0829-313">O <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> é gerado sempre que o valor de <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> alterações.</span><span class="sxs-lookup"><span data-stu-id="f0829-313">The <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event is raised whenever the value of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> changes.</span></span>  
  
 <span data-ttu-id="f0829-314">Em nosso aplicativo, o único elemento que não está usando as configurações do sistema para a cor é o `lblCompanyName`.</span><span class="sxs-lookup"><span data-stu-id="f0829-314">In our application, the only element that is not using the system settings for color is `lblCompanyName`.</span></span> <span data-ttu-id="f0829-315">O <xref:System.Drawing.SystemColors> classe é usada para alterar as configurações de cor do rótulo para as cores do sistema selecionadas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="f0829-315">The <xref:System.Drawing.SystemColors> class is used to change the color settings of the label to the user-selected system colors.</span></span>  
  
#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a><span data-ttu-id="f0829-316">Para habilitar o modo de Alto Contraste de uma maneira eficaz</span><span class="sxs-lookup"><span data-stu-id="f0829-316">To enable High Contrast mode in an effective way</span></span>  
  
1.  <span data-ttu-id="f0829-317">Crie um método para definir as cores do rótulo para as cores do sistema.</span><span class="sxs-lookup"><span data-stu-id="f0829-317">Create a method to set the colors of the label to the system colors.</span></span>  
  
    ```  
    ' Visual Basic  
    Private Sub SetColorScheme()  
       If SystemInformation.HighContrast Then  
          companyLabel.BackColor = SystemColors.Window  
          companyLabel.ForeColor = SystemColors.WindowText  
       Else  
          companyLabel.BackColor = Color.Blue  
          companyLabel.ForeColor = Color.Yellow  
       End If  
    End Sub  
  
    // C#  
    private void SetColorScheme()  
    {  
       if (SystemInformation.HighContrast)  
       {  
          companyLabel.BackColor = SystemColors.Window;  
          companyLabel.ForeColor = SystemColors.WindowText;  
       }  
       else  
       {  
          companyLabel.BackColor = Color.Blue;  
          companyLabel.ForeColor = Color.Yellow;  
       }  
    }  
    ```  
  
2.  <span data-ttu-id="f0829-318">Chame o procedimento `SetColorScheme` no construtor do formulário (`Public Sub New()` no Visual Basic e `public class Form1` no Visual C#).</span><span class="sxs-lookup"><span data-stu-id="f0829-318">Call the `SetColorScheme` procedure in the form constructor (`Public Sub New()` in Visual Basic and `public class Form1` in Visual C#).</span></span> <span data-ttu-id="f0829-319">Para acessar o construtor no Visual Basic, você precisará expandir a região rotulada como **Código gerado pelo Windows Form Designer**.</span><span class="sxs-lookup"><span data-stu-id="f0829-319">To access the constructor in Visual Basic, you will need to expand the region labeled **Windows Form Designer generated code**.</span></span>  
  
    ```  
    ' Visual Basic   
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
    }  
    ```  
  
3.  <span data-ttu-id="f0829-320">Criar um procedimento de evento, com a assinatura apropriada, para responder a <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> eventos.</span><span class="sxs-lookup"><span data-stu-id="f0829-320">Create an event procedure, with the appropriate signature, to respond to the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event.</span></span>  
  
    ```  
    ' Visual Basic  
    Protected Sub UserPreferenceChanged(ByVal sender As Object, _  
    ByVal e As Microsoft.Win32.UserPreferenceChangedEventArgs)  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public void UserPreferenceChanged(object sender,   
    Microsoft.Win32.UserPreferenceChangedEventArgs e)  
    {  
       SetColorScheme();  
    }  
    ```  
  
4.  <span data-ttu-id="f0829-321">Adicione código ao construtor de formulário, após a chamada ao `InitializeComponents`, para associar o procedimento de evento ao evento do sistema.</span><span class="sxs-lookup"><span data-stu-id="f0829-321">Add code to the form constructor, after the call to `InitializeComponents`, to hook up the event procedure to the system event.</span></span> <span data-ttu-id="f0829-322">Esse método chama o procedimento `SetColorScheme`.</span><span class="sxs-lookup"><span data-stu-id="f0829-322">This method calls the `SetColorScheme` procedure.</span></span>  
  
    ```  
    ' Visual Basic  
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
       AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          += new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
    }  
    ```  
  
5.  <span data-ttu-id="f0829-323">Adicione código ao formulário <xref:System.Windows.Forms.Control.Dispose%2A> método antes de chamar o <xref:System.Windows.Forms.Control.Dispose%2A> método da classe base, para liberar o evento quando o aplicativo é fechado.</span><span class="sxs-lookup"><span data-stu-id="f0829-323">Add code to the form <xref:System.Windows.Forms.Control.Dispose%2A> method, before the call to the <xref:System.Windows.Forms.Control.Dispose%2A> method of the base class, to release the event when the application closes.</span></span> <span data-ttu-id="f0829-324">Para acessar o <xref:System.Windows.Forms.Control.Dispose%2A> método no Visual Basic, você precisará expandir a região rotulada como código gerado pelo Windows Form Designer.</span><span class="sxs-lookup"><span data-stu-id="f0829-324">To access the <xref:System.Windows.Forms.Control.Dispose%2A> method in Visual Basic, you will need to expand the region labeled Windows Form Designer generated code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f0829-325">O código de evento do sistema executa um thread separado do aplicativo principal.</span><span class="sxs-lookup"><span data-stu-id="f0829-325">The system event code runs a thread separate from the main application.</span></span> <span data-ttu-id="f0829-326">Se você não liberar o evento, o código que você associou com o evento será executado mesmo depois que o programa for fechado.</span><span class="sxs-lookup"><span data-stu-id="f0829-326">If you do not release the event, the code that you hook up to the event will run even after the program is closed.</span></span>  
  
    ```  
    ' Visual Basic  
    Protected Overloads Overrides Sub Dispose(ByVal disposing As Boolean)  
       If disposing Then  
          If Not (components Is Nothing) Then  
             components.Dispose()  
          End If  
       End If  
       RemoveHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
       MyBase.Dispose(disposing)  
    End Sub  
  
    // C#  
    protected override void Dispose( bool disposing )  
    {  
       if( disposing )  
       {  
          if (components != null)   
          {  
             components.Dispose();  
          }  
       }  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          -= new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
       base.Dispose( disposing );  
    }  
    ```  
  
6.  <span data-ttu-id="f0829-327">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0829-327">Press F5 to run the application.</span></span>  
  
## <a name="conveying-important-information-by-means-other-than-sound"></a><span data-ttu-id="f0829-328">Transmitindo informações importantes por outros meios além do som</span><span class="sxs-lookup"><span data-stu-id="f0829-328">Conveying Important Information by Means Other Than Sound</span></span>  
 <span data-ttu-id="f0829-329">Neste aplicativo, nenhuma informação é transmitida apenas pelo som.</span><span class="sxs-lookup"><span data-stu-id="f0829-329">In this application, no information is conveyed by sound alone.</span></span> <span data-ttu-id="f0829-330">Se você usa som em seu aplicativo, você também deve fornecer as informações por algum outro meio.</span><span class="sxs-lookup"><span data-stu-id="f0829-330">If you use sound in your application, then you should supply the information by some other means as well.</span></span>  
  
#### <a name="to-supply-information-by-some-other-means-than-sound"></a><span data-ttu-id="f0829-331">Para fornecer informações por outros meios além do som</span><span class="sxs-lookup"><span data-stu-id="f0829-331">To supply information by some other means than sound</span></span>  
  
1.  <span data-ttu-id="f0829-332">Faça a barra de título piscar, usando a função FlashWindow da API do Windows.</span><span class="sxs-lookup"><span data-stu-id="f0829-332">Make the title bar flash by using the Windows API function FlashWindow.</span></span> <span data-ttu-id="f0829-333">Para obter um exemplo de como chamar funções da API do Windows, consulte [passo a passo: Chamando APIs do Windows](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span><span class="sxs-lookup"><span data-stu-id="f0829-333">For an example of how to call Windows API functions, see [Walkthrough: Calling Windows APIs](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f0829-334">O usuário pode ter o serviço SoundSentry do Windows habilitado, que também fará com que a janela pisque quando os sons do sistema forem executados pelo alto-falante do computador.</span><span class="sxs-lookup"><span data-stu-id="f0829-334">The user may have the Windows SoundSentry service enabled, which will also cause the window to flash when the system sounds are played through the computer's built-in speaker.</span></span>  
  
2.  <span data-ttu-id="f0829-335">Exiba as informações importantes em uma janela não modal para que o usuário possa responder a elas.</span><span class="sxs-lookup"><span data-stu-id="f0829-335">Display the important information in a non-modal window so that the user may respond to it.</span></span>  
  
3.  <span data-ttu-id="f0829-336">Exiba uma caixa de mensagem que obtém o foco do teclado.</span><span class="sxs-lookup"><span data-stu-id="f0829-336">Display a message box that acquires the keyboard focus.</span></span> <span data-ttu-id="f0829-337">Evite esse método quando o usuário pode estar digitando.</span><span class="sxs-lookup"><span data-stu-id="f0829-337">Avoid this method when the user may be typing.</span></span>  
  
4.  <span data-ttu-id="f0829-338">Exiba um indicador de status na área de notificação de status da barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="f0829-338">Display a status indicator in the status notification area of the taskbar.</span></span> <span data-ttu-id="f0829-339">Para obter detalhes, consulte [Adicionando ícones de aplicativo ao TaskBar com o componente NotifyIcon dos Windows Forms](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="f0829-339">For details, see [Adding Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="f0829-340">Testando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="f0829-340">Testing the Application</span></span>  
 <span data-ttu-id="f0829-341">Antes de implantar o aplicativo, você deve testar os recursos de acessibilidade que implementou.</span><span class="sxs-lookup"><span data-stu-id="f0829-341">Before deploying the application, you should test the accessibility features that you have implemented.</span></span>  
  
#### <a name="to-test-accessibility-features"></a><span data-ttu-id="f0829-342">Para testar os recursos de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="f0829-342">To test accessibility features</span></span>  
  
1.  <span data-ttu-id="f0829-343">Para testar o acesso do teclado, desconecte o mouse e navegue na interface do usuário até cada recurso, usando apenas o teclado.</span><span class="sxs-lookup"><span data-stu-id="f0829-343">To test keyboard access, unplug the mouse and navigate the user interface for each feature using only the keyboard.</span></span> <span data-ttu-id="f0829-344">Certifique-se de que todas as tarefas podem ser realizadas usando apenas o teclado.</span><span class="sxs-lookup"><span data-stu-id="f0829-344">Ensure that all tasks may be performed using the keyboard only.</span></span>  
  
2.  <span data-ttu-id="f0829-345">Para testar o suporte ao Alto Contraste, escolha o ícone de Opções de Acessibilidade no Painel de Controle.</span><span class="sxs-lookup"><span data-stu-id="f0829-345">To test support of High Contrast, choose the Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="f0829-346">Clique na guia Exibir e marque a caixa de seleção Usar Alto Contraste.</span><span class="sxs-lookup"><span data-stu-id="f0829-346">Click the Display tab and select the Use High Contrast check box.</span></span> <span data-ttu-id="f0829-347">Navegue por todos os elementos de interface do usuário para garantir que as alterações de cores e fontes estão refletidas.</span><span class="sxs-lookup"><span data-stu-id="f0829-347">Navigate through all user interface elements to ensure that the color and font changes are reflected.</span></span> <span data-ttu-id="f0829-348">Além disso, verifique se as imagens ou os padrões desenhados atrás do texto estão omitidos.</span><span class="sxs-lookup"><span data-stu-id="f0829-348">Also, ensure that images or patterns drawn behind text are omitted.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f0829-349">O Windows NT 4 não tem um ícone de Opções de Acessibilidade no Painel de Controle.</span><span class="sxs-lookup"><span data-stu-id="f0829-349">Windows NT 4 does not have an Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="f0829-350">Portanto, este procedimento para alterar a configuração SystemInformation.HighContrast não funciona no Windows NT 4.</span><span class="sxs-lookup"><span data-stu-id="f0829-350">Thus, this procedure for changing the SystemInformation.HighContrast setting does not work in Windows NT 4.</span></span>  
  
3.  <span data-ttu-id="f0829-351">Outras ferramentas estão prontamente disponíveis para testar a acessibilidade de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0829-351">Other tools are readily available for testing the accessibility of an application.</span></span>  
  
4.  <span data-ttu-id="f0829-352">Para testar a exposição do foco do teclado, execute a Lupa.</span><span class="sxs-lookup"><span data-stu-id="f0829-352">To test exposing the keyboard focus, run Magnifier.</span></span> <span data-ttu-id="f0829-353">(Para abri-la, clique no menu **Iniciar**, aponte para **Programas**, aponte para **Acessórios**, aponte para **Acessibilidade** e, em seguida, clique em **Lupa**).</span><span class="sxs-lookup"><span data-stu-id="f0829-353">(To open it, click the **Start** menu, point to **Programs**, point to **Accessories**, point to **Accessibility**, and then click **Magnifier**).</span></span> <span data-ttu-id="f0829-354">Navegue na interface do usuário usando as tabulações do teclado e o mouse.</span><span class="sxs-lookup"><span data-stu-id="f0829-354">Navigate the user interface using both keyboard tabbing and the mouse.</span></span> <span data-ttu-id="f0829-355">Verifique se toda a navegação é rastreada corretamente na **Lupa**.</span><span class="sxs-lookup"><span data-stu-id="f0829-355">Ensure that all navigation is tracked properly in **Magnifier**.</span></span>  
  
5.  <span data-ttu-id="f0829-356">Para testar a exposição dos elementos da tela, execute Inspecionar e use o mouse e a tecla TAB para acessar cada elemento.</span><span class="sxs-lookup"><span data-stu-id="f0829-356">To test exposing screen elements, run Inspect, and use both the mouse and the TAB key to reach each element.</span></span> <span data-ttu-id="f0829-357">Verifique se as informações apresentadas nos campos Nome, Estado, Função, Local e Valor da janela Inspecionar são significativas para o usuário para cada objeto na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="f0829-357">Ensure that the information presented in the Name, State, Role, Location, and Value fields of the Inspect window is meaningful to the user for each object in the UI.</span></span>
