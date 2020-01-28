---
title: Associar a um serviço Web usando BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Web services [Windows Forms], binding controls
- BindingSource component [Windows Forms], binding to a Web service
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to Web service
- BindingSource component [Windows Forms], examples
ms.assetid: ee261207-4573-4cb9-a8cb-5185037e0fba
ms.openlocfilehash: 0680c73e578577cf40158761f6c635fe30ff9f4d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746672"
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a>Como associar a um serviço Web usando o BindingSource dos Windows Forms
Se você quiser associar um controle de formulário do Windows aos resultados obtidos da chamada de um Web Service XML, poderá usar um componente <xref:System.Windows.Forms.BindingSource>. Esse procedimento é semelhante a associar um componente de <xref:System.Windows.Forms.BindingSource> a um tipo. É necessário criar um proxy do lado do cliente que contenha os métodos e tipos expostos pelo serviço Web. O proxy do lado do cliente será gerado pelo próprio serviço Web (.asmx) ou pelo arquivo de linguagem WSDL. Além disso, o proxy do lado do cliente deve expor os campos dos tipos complexos usados pelo serviço Web como propriedades públicas. Em seguida, você associa o <xref:System.Windows.Forms.BindingSource> a um dos tipos expostos no proxy do serviço Web.  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a>Criar e associar a um proxy do lado do cliente  
  
1. Crie um formulário do Windows Forms em um diretório de sua escolha, com um namespace apropriado.  
  
2. Adicione um componente <xref:System.Windows.Forms.BindingSource> ao formulário.  
  
3. Abra o prompt de comando do SDK (Software Development Kit) do Windows e navegue até o mesmo diretório em que seu formulário está localizado.  
  
4. Com a ferramenta WSDL, digite `wsdl` e a URL do arquivo .asmx ou WSDL para o serviço Web, seguida pelo namespace do aplicativo e, opcionalmente, o idioma de trabalho.  
  
     O exemplo de código a seguir usa o serviço Web localizado em `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`. Por exemplo, para o tipo `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService` do C# ou para o tipo `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB` do Visual Basic. Passar o caminho como um argumento para a ferramenta WSDL gerará um proxy do lado do cliente no mesmo diretório e namespace do aplicativo, no idioma especificado. Se você estiver usando o Visual Studio, adicione o arquivo ao seu projeto.  
  
5. Selecione um tipo para associar ao proxy do lado do cliente.  
  
     Geralmente, esse é um tipo retornado por um método oferecido pelo serviço Web. Os campos do tipo escolhido devem ser expostos como propriedades públicas para fins de associação.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6. Defina a propriedade <xref:System.Windows.Forms.BindingSource.DataSource%2A> do <xref:System.Windows.Forms.BindingSource> como o tipo que você deseja que esteja contido no proxy do lado do cliente do serviço Web.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a>Associar controles ao BindingSource que está associado a um serviço Web  
  
- Associe os controles à <xref:System.Windows.Forms.BindingSource>, passando a propriedade pública do tipo de serviço Web que você deseja como um parâmetro.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como associar um componente <xref:System.Windows.Forms.BindingSource> a um serviço Web e como associar uma caixa de texto ao componente <xref:System.Windows.Forms.BindingSource>. Ao clicar no botão, um método de serviço Web será chamado e os resultados serão exibidos no `textbox1`.  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este é um exemplo completo que inclui um método `Main` e uma versão abreviada do código de proxy do lado do cliente.  
  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Drawing, System.Web.Services, System.Windows.Forms e System.Xml.  
  
## <a name="see-also"></a>Veja também

- [Componente BindingSource](bindingsource-component.md)
- [Como associar um controle do Windows Forms a um tipo](how-to-bind-a-windows-forms-control-to-a-type.md)
