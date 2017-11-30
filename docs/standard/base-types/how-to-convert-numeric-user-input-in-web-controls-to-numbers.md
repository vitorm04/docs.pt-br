---
title: "Como converter em números as entradas numéricas do usuário em controles da Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 92e28e3b303a7523b9da69b7eb283e0261fc681c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-numeric-user-input-in-web-controls-to-numbers"></a>Como converter em números as entradas numéricas do usuário em controles da Web
Como uma página da Web pode ser exibida em qualquer lugar no mundo, os usuários podem inserir dados numéricos em um <xref:System.Web.UI.WebControls.TextBox> controle em um número quase ilimitado de formatos. Como resultado, é muito importante determinar a localidade e a cultura do usuário da página da Web. Quando você analisar a entrada do usuário, você pode aplicar as convenções de formatação definidas pela localidade e a cultura do usuário.  
  
### <a name="to-convert-numeric-input-from-a-web-textbox-control-to-a-number"></a>Para converter a entrada numérica de um controle de caixa de texto da Web em um número  
  
1.  Determine se a matriz de cadeia de caracteres retornada pelo <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> propriedade é preenchida. Se não estiver, vá para a etapa 6.  
  
2.  Se a matriz de cadeia de caracteres retornada pelo <xref:System.Web.HttpRequest.UserLanguages%2A> propriedade é preenchida, recupere o primeiro elemento. O primeiro elemento indica que o usuário padrão ou idioma e região.  
  
3.  Criar uma instância de um <xref:System.Globalization.CultureInfo> objeto que representa o usuário cultura preferencial do chamando o <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> construtor.  
  
4.  Chame o `TryParse` ou o `Parse` método do tipo numérico que você deseja converter o usuário de entrada. Use uma sobrecarga de `TryParse` ou o `Parse` método com um `provider` parâmetro e passe a ele um dos seguintes:  
  
    -   O <xref:System.Globalization.CultureInfo> objeto criado na etapa 3.  
  
    -   O <xref:System.Globalization.NumberFormatInfo> objeto que é retornado pelo <xref:System.Globalization.CultureInfo.NumberFormat%2A> propriedade o <xref:System.Globalization.CultureInfo> objeto criado na etapa 3.  
  
5.  Se a conversão falhar, repita as etapas 2 a 4 para cada elemento restante na matriz de cadeia de caracteres retornadas pelo <xref:System.Web.HttpRequest.UserLanguages%2A> propriedade.  
  
6.  Se a conversão ainda falhar ou se a matriz de cadeia de caracteres retornada pelo <xref:System.Web.HttpRequest.UserLanguages%2A> propriedade estiver vazia, analise a cadeia de caracteres usando a cultura invariável, que é retornado pelo <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> propriedade.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir é a página de code-behind completa para um formulário da Web que solicita que o usuário insira um valor numérico em um <xref:System.Web.UI.WebControls.TextBox> de controle e o converte em um número. Esse número é dobrado e exibido usando as mesmas regras de formatação da entrada original.  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 O <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> propriedade é preenchida com os nomes de cultura que estão contidos em `Accept-Language` cabeçalhos incluídos em uma solicitação HTTP. No entanto, nem todos os navegadores incluem `Accept-Language` cabeçalhos em suas solicitações e os usuários também podem suprimir os cabeçalhos totalmente. Isso torna importante ter uma cultura de fallback ao analisar a entrada do usuário. Normalmente, a cultura de fallback é a cultura invariável retornada por <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Os usuários também podem fornecer Internet Explorer com nomes de cultura que sua entrada em uma caixa de texto, que cria a possibilidade de que os nomes de cultura podem não ser válidos. Isso torna importante usar tratamento de exceções ao instanciar um <xref:System.Globalization.CultureInfo> objeto.  
  
 Quando recuperados de uma solicitação HTTP enviada pelo Internet Explorer, o <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> matriz é preenchida por ordem de preferência do usuário. O primeiro elemento na matriz contém o nome da cultura/região primária do usuário. Se a matriz contém quaisquer itens adicionais, Internet Explorer arbitrariamente atribui a eles um especificador de qualidade, que é delimitado do nome da cultura por um ponto e vírgula. Por exemplo, uma entrada para a cultura fr-FR pode tomar a forma `fr-FR;q=0.7`.  
  
 O exemplo chama o <xref:System.Globalization.CultureInfo.%23ctor%2A> construtor com seu `useUserOverride` parâmetro definido como `false` para criar um novo <xref:System.Globalization.CultureInfo> objeto. Isso garante que, se o nome de cultura é o nome de cultura padrão no servidor, o novo <xref:System.Globalization.CultureInfo> criado pelo construtor de classe de objeto contém as configurações padrão de uma cultura e não reflete quaisquer configurações substituídas usando o servidor  **Regional e opções de idioma** aplicativo. Os valores de quaisquer configurações substituídas no servidor são provavelmente não existem no sistema do usuário ou sejam refletidas na entrada do usuário.  
  
 Seu código pode chamar tanto o `Parse` ou `TryParse` método do tipo numérico para que a entrada do usuário será convertido em. Chamadas repetidas para um método de análise podem ser necessárias para uma única operação de análise. Como resultado, o `TryParse` método é melhor, porque ele retorna `false` se uma operação de análise falhar. Por outro lado, manipular as exceções repetidas que podem ser geradas pelo `Parse` método pode ser uma proposta muito cara em um aplicativo Web.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Para compilar o código, copie-o para um [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] página code-behind para que ele substitua todo o código existente. O [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] página da Web deve conter os seguintes controles:  
  
-   Um <xref:System.Web.UI.WebControls.Label> controle, que não é referenciado no código. Definir seu <xref:System.Web.UI.WebControls.TextBox.Text%2A> propriedade como "digite um número:".  
  
-   Um <xref:System.Web.UI.WebControls.TextBox> controle chamado `NumericString`.  
  
-   Um <xref:System.Web.UI.WebControls.Button> controle chamado `OKButton`. Definir seu <xref:System.Web.UI.WebControls.Button.Text%2A> propriedade como "Okey".  
  
 Alterar o nome da classe de `NumericUserInput` para o nome da classe que é definido pelo `Inherits` atributo do [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] da página `Page` diretiva. Alterar o nome do `NumericInput` objeto de referência para o nome definido pelo `id` atributo do [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] da página `form` marca.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Para impedir que um usuário insira script no fluxo de HTML, entrada do usuário deve nunca ser ecoada diretamente de volta na resposta do servidor. Em vez disso, ela deve ser codificada usando o <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> método.  
  
## <a name="see-also"></a>Consulte também  
 [Executando operações de formatação](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Analisando cadeias de caracteres numéricas](../../../docs/standard/base-types/parsing-numeric.md)
