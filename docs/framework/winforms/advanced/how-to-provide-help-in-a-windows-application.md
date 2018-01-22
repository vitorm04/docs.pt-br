---
title: Como fornecer ajuda em um aplicativo do Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d23e5d5d19e17aedd37d4d5f6cbc41429463ddfb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-provide-help-in-a-windows-application"></a><span data-ttu-id="8eab1-102">Como fornecer ajuda em um aplicativo do Windows</span><span class="sxs-lookup"><span data-stu-id="8eab1-102">How to: Provide Help in a Windows Application</span></span>
<span data-ttu-id="8eab1-103">Você pode usar o <xref:System.Windows.Forms.HelpProvider> componente anexar tópicos da Ajuda em um arquivo de ajuda a controles específicos em formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="8eab1-103">You can use of the <xref:System.Windows.Forms.HelpProvider> component to attach Help topics within a Help file to specific controls on Windows Forms.</span></span> <span data-ttu-id="8eab1-104">O arquivo de Ajuda pode ser HTML ou HTMLHelp 1.x ou formato maior.</span><span class="sxs-lookup"><span data-stu-id="8eab1-104">The Help file can be either HTML or HTMLHelp 1.x or greater format.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8eab1-105">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="8eab1-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8eab1-106">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="8eab1-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8eab1-107">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="8eab1-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-provide-help"></a><span data-ttu-id="8eab1-108">Para fornecer Ajuda</span><span class="sxs-lookup"><span data-stu-id="8eab1-108">To provide Help</span></span>  
  
1.  <span data-ttu-id="8eab1-109">Do **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.HelpProvider> componente para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="8eab1-109">From the **Toolbox**, drag a <xref:System.Windows.Forms.HelpProvider> component to your form.</span></span>  
  
     <span data-ttu-id="8eab1-110">O componente ficará na bandeja na parte inferior do Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="8eab1-110">The component will reside in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="8eab1-111">No **propriedades** janela, defina o <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> propriedade para o arquivo de Ajuda. chm,. col ou. htm.</span><span class="sxs-lookup"><span data-stu-id="8eab1-111">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property to the .chm, .col, or .htm Help file.</span></span>  
  
3.  <span data-ttu-id="8eab1-112">Selecione outro controle que você tem em seu formulário e, no **propriedades** janela, defina o <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="8eab1-112">Select another control you have on your form, and in the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> property.</span></span>  
  
     <span data-ttu-id="8eab1-113">Isso é a cadeia de caracteres passada a <xref:System.Windows.Forms.HelpProvider> componente ao seu arquivo de ajuda para chamar o tópico de Ajuda apropriado.</span><span class="sxs-lookup"><span data-stu-id="8eab1-113">This is the string passed through the <xref:System.Windows.Forms.HelpProvider> component to your Help file to summon the appropriate Help topic.</span></span>  
  
4.  <span data-ttu-id="8eab1-114">No **propriedades** janela, defina o <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> propriedade com um valor da <xref:System.Windows.Forms.HelpNavigator> enumeração.</span><span class="sxs-lookup"><span data-stu-id="8eab1-114">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> property to a value of the <xref:System.Windows.Forms.HelpNavigator> enumeration.</span></span>  
  
     <span data-ttu-id="8eab1-115">Isso determina o modo como a propriedade **HelpKeyword** é passada para o sistema de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="8eab1-115">This determines the way in which the **HelpKeyword** property is passed to the Help system.</span></span> <span data-ttu-id="8eab1-116">A tabela a seguir mostra as possíveis configurações e suas descrições.</span><span class="sxs-lookup"><span data-stu-id="8eab1-116">The following table shows the possible settings and their descriptions.</span></span>  
  
    |<span data-ttu-id="8eab1-117">Nome do Membro</span><span class="sxs-lookup"><span data-stu-id="8eab1-117">Member Name</span></span>|<span data-ttu-id="8eab1-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="8eab1-118">Description</span></span>|  
    |-----------------|-----------------|  
    |<span data-ttu-id="8eab1-119">AssociateIndex</span><span class="sxs-lookup"><span data-stu-id="8eab1-119">AssociateIndex</span></span>|<span data-ttu-id="8eab1-120">Especifica que o índice para um tópico especificado é realizado na URL especificada.</span><span class="sxs-lookup"><span data-stu-id="8eab1-120">Specifies that the index for a specified topic is performed in the specified URL.</span></span>|  
    |<span data-ttu-id="8eab1-121">Localizar</span><span class="sxs-lookup"><span data-stu-id="8eab1-121">Find</span></span>|<span data-ttu-id="8eab1-122">Especifica que a página de pesquisa de uma URL especificada é exibida.</span><span class="sxs-lookup"><span data-stu-id="8eab1-122">Specifies that the search page of a specified URL is displayed.</span></span>|  
    |<span data-ttu-id="8eab1-123">Índice</span><span class="sxs-lookup"><span data-stu-id="8eab1-123">Index</span></span>|<span data-ttu-id="8eab1-124">Especifica que o índice de uma URL especificada é exibido.</span><span class="sxs-lookup"><span data-stu-id="8eab1-124">Specifies that the index of a specified URL is displayed.</span></span>|  
    |<span data-ttu-id="8eab1-125">KeywordIndex</span><span class="sxs-lookup"><span data-stu-id="8eab1-125">KeywordIndex</span></span>|<span data-ttu-id="8eab1-126">Especifica uma palavra-chave para pesquisar e a ação a ser tomada na URL especificada.</span><span class="sxs-lookup"><span data-stu-id="8eab1-126">Specifies a keyword to search for and the action to take in the specified URL.</span></span>|  
    |<span data-ttu-id="8eab1-127">TableOfContents</span><span class="sxs-lookup"><span data-stu-id="8eab1-127">TableOfContents</span></span>|<span data-ttu-id="8eab1-128">Especifica que o sumário do arquivo de Ajuda HTML 1.0 é exibido.</span><span class="sxs-lookup"><span data-stu-id="8eab1-128">Specifies that the table of contents of the HTML 1.0 Help file is displayed.</span></span>|  
    |<span data-ttu-id="8eab1-129">Tópico</span><span class="sxs-lookup"><span data-stu-id="8eab1-129">Topic</span></span>|<span data-ttu-id="8eab1-130">Especifica que o tópico referenciado por uma URL especificada é exibido.</span><span class="sxs-lookup"><span data-stu-id="8eab1-130">Specifies that the topic referenced by the specified URL is displayed.</span></span>|  
  
 <span data-ttu-id="8eab1-131">Em tempo de execução, pressionando F1 quando o controle — para que você tenha definido a **HelpKeyword** e **HelpNavigator** propriedades — tem foco irá abrir o arquivo de ajuda associado que <xref:System.Windows.Forms.HelpProvider> componente.</span><span class="sxs-lookup"><span data-stu-id="8eab1-131">At run time, pressing F1 when the control—for which you have set the **HelpKeyword** and **HelpNavigator** properties—has focus will open the Help file you associated with that <xref:System.Windows.Forms.HelpProvider> component.</span></span>  
  
 <span data-ttu-id="8eab1-132">Atualmente, a propriedade **HelpNamespace** dá suporte a arquivos de Ajuda nos três formatos a seguir: HTMLHelp 1.x, HTMLHelp 2.0 e HTML.</span><span class="sxs-lookup"><span data-stu-id="8eab1-132">Currently, the **HelpNamespace** property supports Help files in the following three formats: HTMLHelp 1.x, HTMLHelp 2.0, and HTML.</span></span> <span data-ttu-id="8eab1-133">Assim, você pode definir a propriedade **HelpNamespace** para um endereço http://, como uma página da Web.</span><span class="sxs-lookup"><span data-stu-id="8eab1-133">Thus, you can set the **HelpNamespace** property to an http:// address, such as a Web page.</span></span> <span data-ttu-id="8eab1-134">Se isso for feito, abrirá o navegador padrão para a página da Web com a cadeia de caracteres especificada na propriedade **HelpKeyword** usada como âncora.</span><span class="sxs-lookup"><span data-stu-id="8eab1-134">If this is done, it will open the default browser to the Web page with the string specified in the **HelpKeyword** property used as the anchor.</span></span> <span data-ttu-id="8eab1-135">A âncora é usada para ir para uma parte específica de uma página HTML.</span><span class="sxs-lookup"><span data-stu-id="8eab1-135">The anchor is used to jump to a specific part of an HTML page.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8eab1-136">Tenha cuidado para verificar as informações que são enviadas de um cliente antes de usá-las em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8eab1-136">Be careful to check any information that is sent from a client before using it in your application.</span></span> <span data-ttu-id="8eab1-137">Usuários mal-intencionados podem tentar enviar ou injetar script executável, instruções SQL ou outro código.</span><span class="sxs-lookup"><span data-stu-id="8eab1-137">Malicious users might try to send or inject executable script, SQL statements, or other code.</span></span> <span data-ttu-id="8eab1-138">Antes de exibir a entrada do usuário, armazená-la em um banco de dados ou trabalhar com ela, verifique se ela não contém informações potencialmente não seguras.</span><span class="sxs-lookup"><span data-stu-id="8eab1-138">Before you display a user's input, store it in a database, or work with it, check that it does not contain potentially unsafe information.</span></span> <span data-ttu-id="8eab1-139">Uma maneira comum de verificar é usar uma expressão regular para procurar palavras-chave como "SCRIPT" ao receber entrada de um usuário.</span><span class="sxs-lookup"><span data-stu-id="8eab1-139">A typical way to check is to use a regular expression to look for keywords such as "SCRIPT" when you receive input from a user.</span></span>  
  
 <span data-ttu-id="8eab1-140">Você também pode usar o <xref:System.Windows.Forms.HelpProvider> componente para exibir ajuda pop-up, mesmo se você tiver configurado para exibir arquivos de ajuda para os controles em seus formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="8eab1-140">You can also use the <xref:System.Windows.Forms.HelpProvider> component to show pop-up Help, even if you have it configured to display Help files for the controls on your Windows Forms.</span></span> <span data-ttu-id="8eab1-141">Para obter mais informações, consulte [Como exibir Ajuda em pop-up](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span><span class="sxs-lookup"><span data-stu-id="8eab1-141">For more information, see [How to: Display Pop-up Help](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eab1-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8eab1-142">See Also</span></span>  
 [<span data-ttu-id="8eab1-143">Como Exibir Ajuda Pop-up</span><span class="sxs-lookup"><span data-stu-id="8eab1-143">How to: Display Pop-up Help</span></span>](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)  
 [<span data-ttu-id="8eab1-144">Ajuda de Controle Usando ToolTips</span><span class="sxs-lookup"><span data-stu-id="8eab1-144">Control Help Using ToolTips</span></span>](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [<span data-ttu-id="8eab1-145">Integrando a Ajuda do Usuário nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8eab1-145">Integrating User Help in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [<span data-ttu-id="8eab1-146">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8eab1-146">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
