---
title: "Como associar a um serviço Web usando o BindingSource dos Windows Forms"
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
- Web services [Windows Forms], binding controls
- BindingSource component [Windows Forms], binding to a Web service
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to Web service
- BindingSource component [Windows Forms], examples
ms.assetid: ee261207-4573-4cb9-a8cb-5185037e0fba
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5024ad9000811aa438183de240c91b659644a7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a>Como associar a um serviço Web usando o BindingSource dos Windows Forms
Se você deseja associar um controle de formulário do Windows para os resultados obtidos de chamar um serviço Web XML, você pode usar um <xref:System.Windows.Forms.BindingSource> componente. Esse procedimento é semelhante à associação de um <xref:System.Windows.Forms.BindingSource> um tipo de componente. É necessário criar um proxy do lado do cliente que contenha os métodos e tipos expostos pelo serviço Web. O proxy do lado do cliente será gerado pelo próprio serviço Web (.asmx) ou pelo arquivo de linguagem WSDL. Além disso, o proxy do lado do cliente deve expor os campos dos tipos complexos usados pelo serviço Web como propriedades públicas. Em seguida, associar a <xref:System.Windows.Forms.BindingSource> para um dos tipos expostos na Web proxy de serviço.  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a>Criar e associar a um proxy do lado do cliente  
  
1.  Crie um formulário do Windows Forms em um diretório de sua escolha, com um namespace apropriado.  
  
2.  Adicionar um <xref:System.Windows.Forms.BindingSource> componente para o formulário.  
  
3.  Abra o prompt de comando [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] e acesse o mesmo diretório em que o formulário está localizado.  
  
4.  Com a ferramenta WSDL, digite `wsdl` e a URL do arquivo .asmx ou WSDL para o serviço Web, seguida pelo namespace do aplicativo e, opcionalmente, o idioma de trabalho.  
  
     O exemplo de código a seguir usa o serviço Web localizado em http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx. Por exemplo, para o tipo `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService` do C# ou para o tipo `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB` do Visual Basic. Passar o caminho como um argumento para a ferramenta WSDL gerará um proxy do lado do cliente no mesmo diretório e namespace do aplicativo, no idioma especificado. Se [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] estiver sendo usado, adicione o arquivo ao projeto.  
  
5.  Selecione um tipo para associar ao proxy do lado do cliente.  
  
     Geralmente, esse é um tipo retornado por um método oferecido pelo serviço Web. Os campos do tipo escolhido devem ser expostos como propriedades públicas para fins de associação.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6.  Definir o <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriedade o <xref:System.Windows.Forms.BindingSource> para o tipo que você deseja que é contida no proxy de cliente do serviço Web.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a>Associar controles ao BindingSource que está associado a um serviço Web  
  
-   Vincular controles a <xref:System.Windows.Forms.BindingSource>, passando a propriedade pública do tipo de serviço da Web que você deseja como um parâmetro.  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como associar um <xref:System.Windows.Forms.BindingSource> componente a um serviço Web e como associar uma caixa de texto para o <xref:System.Windows.Forms.BindingSource> componente. Ao clicar no botão, um método de serviço Web será chamado e os resultados serão exibidos no `textbox1`.  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este é um exemplo completo que inclui um método `Main` e uma versão abreviada do código de proxy do lado do cliente.  
  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Drawing, System.Web.Services, System.Windows.Forms e System.Xml.  
  
 Para obter informações sobre como compilar este exemplo na linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line (Compilando na linha de comando)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Compilando pela linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.  Consulte também [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) (Como compilar e executar um exemplo completo de código dos Windows Forms usando o Visual Studio).  
  
## <a name="see-also"></a>Consulte também  
 [Componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Como associar um controle dos Windows Forms a um tipo](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
