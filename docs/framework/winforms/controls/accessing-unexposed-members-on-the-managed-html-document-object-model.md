---
title: Acessando membros não expostos no Document Object Model HTML gerenciado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
ms.openlocfilehash: 20341a44eb8a43a9d130e0b76d23b513738c6782
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129500"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>Acessando membros não expostos no Document Object Model HTML gerenciado
O gerenciado HTML documento Object Model (DOM) contém uma classe chamada <xref:System.Windows.Forms.HtmlElement> que expõe as propriedades, métodos e eventos que todos os elementos HTML têm em comum. Às vezes, no entanto, será necessário acessar membros que a interface gerenciada não expõe diretamente. Este tópico analisa duas maneiras de acessar membros não expostos, incluindo [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] e funções do VBScript definidas dentro de uma página da Web.  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>Acessando Membros Não Expostos por meio de Interfaces Gerenciadas  
 <xref:System.Windows.Forms.HtmlDocument> e <xref:System.Windows.Forms.HtmlElement> fornecem quatro métodos que permitem o acesso a membros não expostos. A tabela a seguir mostra os tipos e seus métodos correspondentes.  
  
|Tipo do membro|Método(s)|  
|-----------------|-----------------|  
|Propriedades (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|Métodos|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|Events (<xref:System.Windows.Forms.HtmlDocument>)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|Events (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|Events (<xref:System.Windows.Forms.HtmlWindow>)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 Ao usar esses métodos, presume-se que se tem um elemento do tipo subjacente correto. Suponha que você queira escutar o evento `Submit` de um elemento `FORM` em uma página HTML, para que seja possível executar o pré-processamento nos valores de `FORM` antes de o usuário enviá-los para o servidor. Teoricamente, se tiver controle sobre a HTML, você definirá que o `FORM` terá um atributo `ID` único.  
  
```  
<HTML>  
  
    <HEAD>  
        <TITLE>Form Page</TITLE>  
    </HEAD>  
  
    <BODY>  
        <FORM ID="form1">  
             ... form fields defined here ...  
        </FORM>  
    </BODY>  
  
</HTML>  
```  
  
 Depois que você carregar esta página para o <xref:System.Windows.Forms.WebBrowser> controle, você pode usar o <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> método para recuperar o `FORM` em tempo de execução usando `form1` como o argumento.  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a>Acessando as Interfaces Não Gerenciadas  
 Também é possível acessar membros não expostos no HTML DOM gerenciado usando as interfaces Component Object Model (COM) não gerenciadas expostas por cada classe DOM. Isso será recomendado se for necessário fazer várias chamadas em membros não expostos ou se os membros não expostos retornarem outras interfaces não gerenciadas não encapsuladas pelo o HTML DOM gerenciado.  
  
 A tabela a seguir mostra todas as interfaces não gerenciadas expostas por meio do HTML DOM gerenciado. Clique em cada link para obter uma explicação de seu uso e exemplos de código.  
  
|Tipo|Interface não gerenciada|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 A maneira mais fácil de usar as interfaces COM é adicionar uma referência à biblioteca de HTML DOM não gerenciada (MSHTML.dll) por meio do aplicativo, embora não haja suporte para isso. Para obter mais informações, consulte o [Artigo 934368 da base de dados de conhecimento](https://support.microsoft.com/kb/934368).  
  
## <a name="accessing-script-functions"></a>Acessando Funções de Script  
 Uma página HTML pode definir uma ou mais funções usando uma linguagem de script como [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] ou VBScript. Essas funções são colocadas dentro de uma página `SCRIPT` na página e podem ser executadas sob demanda ou em resposta a um evento no DOM.  
  
 Você pode chamar quaisquer funções de script que você define em uma página HTML usando o <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> método. Se o método de script retorna um elemento HTML, você pode usar uma conversão para converter o resultado retornado para um <xref:System.Windows.Forms.HtmlElement>. Para obter detalhes e o código de exemplo, consulte <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.  
  
## <a name="see-also"></a>Consulte também

- [Usando o Document Object Model HTML gerenciado](using-the-managed-html-document-object-model.md)
