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
ms.openlocfilehash: 525ef52ecbbc61fba787fa8286c56c638d837faf
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988397"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>Acessando membros não expostos no Document Object Model HTML gerenciado
O modelo de objeto do documento HTML gerenciado (dom) contém uma classe chamada <xref:System.Windows.Forms.HtmlElement> que expõe as propriedades, os métodos e os eventos que todos os elementos HTML têm em comum. Às vezes, no entanto, será necessário acessar membros que a interface gerenciada não expõe diretamente. Este tópico examina duas maneiras de acessar membros não expostos, incluindo as funções JScript e VBScript definidas dentro de uma página da Web.  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>Acessando Membros Não Expostos por meio de Interfaces Gerenciadas  
 <xref:System.Windows.Forms.HtmlDocument>e <xref:System.Windows.Forms.HtmlElement> fornecem quatro métodos que habilitam o acesso a membros não expostos. A tabela a seguir mostra os tipos e seus métodos correspondentes.  
  
|Tipo do membro|Método(s)|  
|-----------------|-----------------|  
|Propriedades (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|Métodos|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|Eventos (<xref:System.Windows.Forms.HtmlDocument>)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|Eventos (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|Eventos (<xref:System.Windows.Forms.HtmlWindow>)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 Ao usar esses métodos, presume-se que se tem um elemento do tipo subjacente correto. Suponha que você queira escutar o evento `Submit` de um elemento `FORM` em uma página HTML, para que seja possível executar o pré-processamento nos valores de `FORM` antes de o usuário enviá-los para o servidor. Teoricamente, se tiver controle sobre a HTML, você definirá que o `FORM` terá um atributo `ID` único.  
  
```html  
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
  
 Depois de <xref:System.Windows.Forms.WebBrowser> carregar essa página no controle, você pode usar o <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> método para recuperar o `FORM` em tempo de execução usando `form1` como o argumento.  
  
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
 Uma página HTML pode definir uma ou mais funções usando uma linguagem de script, como JScript ou VBScript. Essas funções são colocadas dentro de uma página `SCRIPT` na página e podem ser executadas sob demanda ou em resposta a um evento no DOM.  
  
 Você pode chamar qualquer função de script que definir em uma página HTML usando <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> o método. Se o método de script retornar um elemento HTML, você poderá usar uma conversão para converter esse resultado de retorno <xref:System.Windows.Forms.HtmlElement>em um. Para obter detalhes e código de exemplo <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>, consulte.  
  
## <a name="see-also"></a>Consulte também

- [Usando o Modelo de Objeto do Documento HTML gerenciado](using-the-managed-html-document-object-model.md)
