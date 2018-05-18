---
title: Como converter em números as entradas numéricas do usuário em controles da Web
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- parsing strings [.NET Framework], numeric strings
- converting numeric user input to number
- numbers [.NET Framework], converting numeric user input to number
ms.assetid: f27ddfb8-7479-4b79-8879-02a3bd8402d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24016ea68e17aa66432928c43d1de970fc13a55b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-numeric-user-input-in-web-controls-to-numbers"></a>Como converter em números as entradas numéricas do usuário em controles da Web
Como uma página da Web pode ser exibida em qualquer lugar no mundo, os usuários podem inserir dados numéricos em um controle de <xref:System.Web.UI.WebControls.TextBox> em um número quase ilimitado de formatos. Como resultado, é muito importante determinar a localidade e a cultura do usuário da página da Web. Quando você analisa a entrada do usuário, pode aplicar as convenções de formatação definidas pela localidade e a cultura do usuário.  
  
### <a name="to-convert-numeric-input-from-a-web-textbox-control-to-a-number"></a>Para converter a entrada numérica de um controle de caixa de texto da Web em um número  
  
1.  Determine se a matriz de cadeia de caracteres retornada pela propriedade <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> é populada. Se não for, vá para a etapa 6.  
  
2.  Se a matriz de cadeia de caracteres retornada pela propriedade <xref:System.Web.HttpRequest.UserLanguages%2A> for populada, recupere o primeiro elemento. O primeiro elemento indica o idioma e a região padrão ou preferenciais do usuário.  
  
3.  Crie uma instância de um objeto <xref:System.Globalization.CultureInfo> que represente a cultura preferencial do usuário do chamando o construtor <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>.  
  
4.  Chame o método `TryParse` ou `Parse` do tipo numérico para o qual você deseja converter a entrada do usuário. Use uma sobrecarga do método `TryParse` ou `Parse` com um parâmetro `provider` e passe para ele um dos seguintes itens:  
  
    -   O objeto <xref:System.Globalization.CultureInfo> criado na etapa 3.  
  
    -   O objeto <xref:System.Globalization.NumberFormatInfo> que é retornado pela propriedade <xref:System.Globalization.CultureInfo.NumberFormat%2A> do objeto <xref:System.Globalization.CultureInfo> criado na etapa 3.  
  
5.  Se a conversão falhar, repita as etapas 2 a 4 para cada elemento restante na matriz de cadeia de caracteres retornada pela propriedade <xref:System.Web.HttpRequest.UserLanguages%2A>.  
  
6.  Se a conversão ainda falhar ou se a matriz de cadeia de caracteres retornada pela propriedade <xref:System.Web.HttpRequest.UserLanguages%2A> estiver vazia, analise a cadeia de caracteres usando a cultura invariável, que é retornada pela propriedade <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir é a página code-behind completa para um formulário da Web que solicita que o usuário insira um valor numérico em um controle de <xref:System.Web.UI.WebControls.TextBox> e o converta em um número. Esse número é dobrado e exibido usando as mesmas regras de formatação da entrada original.  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 A propriedade <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> é populada com os nomes de cultura que estão contidos em cabeçalhos `Accept-Language` incluídos em uma solicitação HTTP. No entanto, nem todos os navegadores incluem cabeçalhos `Accept-Language` em suas solicitações, e os usuários também podem suprimir totalmente os cabeçalhos. Por isso, é importante ter uma cultura de fallback ao analisar a entrada do usuário. Normalmente, a cultura de fallback é a cultura invariável retornada por <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Os usuários também podem fornecer ao Internet Explorer nomes de cultura que inserem em uma caixa de texto, o que cria a possibilidade de que os nomes de cultura não sejam válidos. Assim, é importante usar o tratamento de exceções ao instanciar um objeto <xref:System.Globalization.CultureInfo>.  
  
 Quando recuperada de uma solicitação HTTP enviada pelo Internet Explorer, a matriz <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> é populada por ordem de preferência do usuário. O primeiro elemento na matriz contém o nome da cultura/região principal do usuário. Se a matriz contiver itens adicionais, o Internet Explorer atribuirá arbitrariamente a eles um especificador de qualidade, que é delimitado do nome da cultura por um ponto e vírgula. Por exemplo, uma entrada para a cultura fr-FR pode ter o formato `fr-FR;q=0.7`.  
  
 O exemplo chama o construtor <xref:System.Globalization.CultureInfo.%23ctor%2A> com o parâmetro `useUserOverride` definido como `false` para criar um novo objeto <xref:System.Globalization.CultureInfo>. Isso garante que, se o nome de cultura for o nome de cultura padrão no servidor, o novo <xref:System.Globalization.CultureInfo> criado pelo construtor de classe de objeto conterá as configurações padrão de uma cultura e não refletirá configurações substituídas usando o aplicativo **Opções Regionais e de Idioma** do servidor. Os valores de configurações substituídas no servidor provavelmente não existem no sistema do usuário nem são refletidos na entrada do usuário.  
  
 Seu código pode chamar o método `Parse` ou `TryParse` do tipo numérico para o qual a entrada do usuário será convertida. As chamadas repetidas para um método de análise podem ser necessárias para uma única operação de análise. Como resultado, o método `TryParse` é melhor porque retorna `false` se uma operação de análise falha. Por outro lado, manipular as exceções repetidas que podem ser geradas pelo método `Parse` pode ser uma proposta muito cara em um aplicativo Web.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Para compilar o código, copie-o para uma página code-behind [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] para que ele substitua todo o código existente. A página da Web [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] deve conter os seguintes controles:  
  
-   Um controle <xref:System.Web.UI.WebControls.Label>, que não é referenciado no código. Defina a propriedade <xref:System.Web.UI.WebControls.TextBox.Text%2A> como "Digite um Número:".  
  
-   Um controle <xref:System.Web.UI.WebControls.TextBox> chamado `NumericString`.  
  
-   Um controle <xref:System.Web.UI.WebControls.Button> chamado `OKButton`. Defina sua propriedade <xref:System.Web.UI.WebControls.Button.Text%2A> como "OK".  
  
 Alterar o nome da classe de `NumericUserInput` para o nome da classe que é definido pelo atributo `Inherits` da diretiva `Page` da página do [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]. Alterar o nome da referência do objeto `NumericInput` para o nome definido pelo atributo `id` da marca `form` da página do [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Para impedir que um usuário insira script no fluxo de HTML, a entrada do usuário nunca deve ser ecoada diretamente de volta na resposta do servidor. Em vez disso, ela deve ser codificada usando o método <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também  
 [Executando operações de formatação](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Analisando cadeias de caracteres numéricas](../../../docs/standard/base-types/parsing-numeric.md)
