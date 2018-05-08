---
title: Acessando quadros no Document Object Model HTML gerenciado
ms.date: 03/30/2017
helpviewer_keywords:
- HTML [Windows Forms], dOM
- managed HTML DOM
- HTML [Windows Forms], managed
- HTML DOM [Windows Forms], managed
- frames [Windows Forms], accessing
- DOM [Windows Forms], accessing frames in managed HTML
ms.assetid: cdeeaa22-0be4-4bbf-9a75-4ddc79199f8d
ms.openlocfilehash: a9bd6bb730ff84a48c180c7f1ac435afbf75fbc0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-frames-in-the-managed-html-document-object-model"></a>Acessando quadros no Document Object Model HTML gerenciado
Alguns documentos HTML são compostos de *quadros* ou janelas que podem manter seus próprios documentos HTML distintos. Usar quadros facilita a criação de páginas HTML na qual uma ou mais partes da página permanecem estáticas, como uma barra de navegação, enquanto outros quadros alterar seu conteúdo constantemente.  
  
 Criadores de HTML podem criar quadros de duas maneiras:  
  
-   Usando as marcas `FRAMESET` e `FRAME`, que criam janelas fixas.  
  
 -ou-  
  
-   Usando a marca `IFRAME`, que cria uma janela flutuante que pode ser reposicionada em tempo de execução.  
  
1.  Como os quadros contêm documentos HTML, eles são representados no Modelo de Objeto do Documento (DOM) como elementos de janela e de quadro.  
  
2.  Quando você acessa um `FRAME` ou `IFRAME` marca usando a coleção de quadros de <xref:System.Windows.Forms.HtmlWindow>, você está recuperando o elemento correspondente ao quadro da janela. Isso representa todas as propriedades dinâmicas do quadro, como sua URL, documento e tamanho atual.  
  
3.  Quando você acessa um `FRAME` ou `IFRAME` marca usando o <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> propriedade <xref:System.Windows.Forms.HtmlWindow>, o <xref:System.Windows.Forms.HtmlElement.Children%2A> coleção ou métodos, como <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> ou <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>, você está recuperando o elemento de quadro. Isso representa as propriedades estáticas do quadro, incluindo a URL especificada no arquivo HTML original.  
  
## <a name="frames-and-security"></a>Quadros e Segurança  
 O acesso aos quadros é complicado pelo fato de que o HTML DOM gerenciado implementa uma medida de segurança, conhecida como *segurança de scripts entre quadros*. Se um documento contiver um `FRAMESET` com duas ou mais `FRAME`s em domínios diferentes, esses `FRAME`s não poderão interagir entre si. Em outras palavras, uma `FRAME` que exibe o conteúdo do site não pode acessar informações em um `FRAME` que hospeda um site de terceiros, como http://www.adatum.com/. Essa segurança é implementada no nível do <xref:System.Windows.Forms.HtmlWindow> classe. Você pode obter informações gerais sobre um `FRAME` hospedagem outro site da Web, como a URL, mas não poderão acessar seu <xref:System.Windows.Forms.HtmlWindow.Document%2A> ou alterar o tamanho ou local de sua hospedagem `FRAME` ou `IFRAME`.  
  
 Esta regra também se aplica ao windows que você abre usando o <xref:System.Windows.Forms.HtmlWindow.Open%2A> e <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A> métodos. Se a janela abrir está em um domínio diferente da página hospedada no <xref:System.Windows.Forms.WebBrowser> controle, você não poderá mover a janela ou examinar o conteúdo. Essas restrições são aplicadas também se você usar o <xref:System.Windows.Forms.WebBrowser> controle para exibir um site que é diferente do site da Web usado para implantar seu aplicativo com base em formulários do Windows. Se você usar [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] tecnologia de implantação para instalar o aplicativo do site da Web A e você usar o <xref:System.Windows.Forms.WebBrowser> para exibir o site da Web B, não será capaz de dados do site de acesso do B.  
  
 Para obter mais informações sobre a segurança de scripts entre sites, consulte[Sobre Scripts Entre Quadros e Segurança](http://msdn.microsoft.com/library/ms533028.aspx).  
  
## <a name="see-also"></a>Consulte também  
 [Elemento de quadro &#124; objeto do quadro](http://msdn.microsoft.com/library/ms535250.aspx)  
 [Usando o Modelo de Objeto do Documento HTML gerenciado](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
