---
title: "Como exibir informações localizadas de data e hora para usuários da Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- formatting [.NET Framework], dates
- parsing strings [.NET Framework], date and time strings
- localization [.NET Framework], date and time displays
- formatting [.NET Framework], localized data
- displaying date and time data
- localized date displays [.NET Framework]
ms.assetid: 377fe93c-32be-421a-a30a-be639a46ede8
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 21493e0e0c9e42cf5efc42d86c8f126fbae9b392
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-localized-date-and-time-information-to-web-users"></a>Como exibir informações localizadas de data e hora para usuários da Web
Como uma página da Web pode ser exibida em qualquer lugar no mundo, operações de analisar e Formatar valores de data e hora não devem confiar em um formato padrão (que geralmente é o formato da cultura local do servidor Web) ao interagir com o usuário. Em vez disso, formulários da Web que lidar com a data e hora cadeias de caracteres inseridas pelo usuário devem analisar as cadeias de caracteres usando a cultura preferencial do usuário. Da mesma forma, os dados de data e hora devem ser exibidos para o usuário em um formato compatível com a cultura do usuário. Este tópico mostra como fazer isso.  
  
### <a name="to-parse-date-and-time-strings-input-by-the-user"></a>Ao analisar a data e hora em cadeias de caracteres de entrada do usuário  
  
1.  Determine se a matriz de cadeia de caracteres retornada pelo <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> propriedade é preenchida. Se não estiver, vá para a etapa 6.  
  
2.  Se a matriz de cadeia de caracteres retornada pelo <xref:System.Web.HttpRequest.UserLanguages%2A> propriedade é preenchida, recupere o primeiro elemento. O primeiro elemento indica que o usuário padrão ou idioma e região.  
  
3.  Criar uma instância de um <xref:System.Globalization.CultureInfo> objeto que representa o usuário cultura preferencial do chamando o <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> construtor.  
  
4.  Chame o `TryParse` ou o `Parse` método o <xref:System.DateTime> ou <xref:System.DateTimeOffset> tipo para tentar a conversão. Use uma sobrecarga de `TryParse` ou o `Parse` método com um `provider` parâmetro e passe a ele um dos seguintes:  
  
    -   O <xref:System.Globalization.CultureInfo> objeto criado na etapa 3.  
  
    -   O <xref:System.Globalization.DateTimeFormatInfo> objeto que é retornado pelo <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> propriedade o <xref:System.Globalization.CultureInfo> objeto criado na etapa 3.  
  
5.  Se a conversão falhar, repita as etapas 2 a 4 para cada elemento restante na matriz de cadeia de caracteres retornadas pelo <xref:System.Web.HttpRequest.UserLanguages%2A> propriedade.  
  
6.  Se a conversão ainda falhar ou se a matriz de cadeia de caracteres retornada pelo <xref:System.Web.HttpRequest.UserLanguages%2A> propriedade estiver vazia, analise a cadeia de caracteres usando a cultura invariável, que é retornado pelo <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> propriedade.  
  
### <a name="to-parse-the-local-date-and-time-of-the-users-request"></a>Ao analisar a data e hora local da solicitação do usuário  
  
1.  Adicionar um <xref:System.Web.UI.WebControls.HiddenField> a um formulário da Web.  
  
2.  Criar uma função JavaScript que manipula o `onClick` eventos de um `Submit` botão escrevendo a data e hora atuais e deslocamento do fuso horário local do tempo Universal Coordenado (UTC) para o <xref:System.Web.UI.WebControls.HiddenField.Value%2A> propriedade. Use um delimitador (como um ponto e vírgula) para separar os dois componentes da cadeia de caracteres.  
  
3.  Use o formulário de Web <xref:System.Web.UI.Control.PreRender> fluxo de saída de evento para inserir a função no HTML, passando o texto do script para o <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType> método.  
  
4.  Conecte-se o manipulador de eventos para o `Submit` do botão `onClick` evento, fornecendo o nome da função JavaScript a ser o `OnClientClick` atributo do `Submit` botão.  
  
5.  Criar um manipulador para o `Submit` do botão <xref:System.Web.UI.WebControls.Button.Click> eventos.  
  
6.  No manipulador de eventos, determine se a matriz de cadeia de caracteres retornada pelo <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> propriedade é preenchida. Se não estiver, vá para a etapa 14.  
  
7.  Se a matriz de cadeia de caracteres retornada pelo <xref:System.Web.HttpRequest.UserLanguages%2A> propriedade é preenchida, recupere o primeiro elemento. O primeiro elemento indica que o usuário padrão ou idioma e região.  
  
8.  Criar uma instância de um <xref:System.Globalization.CultureInfo> objeto que representa o usuário cultura preferencial do chamando o <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> construtor.  
  
9. Passe a cadeia de caracteres atribuída ao <xref:System.Web.UI.WebControls.HiddenField.Value%2A> propriedade para o <xref:System.String.Split%2A> método para armazenar a representação de cadeia de caracteres de data local do usuário e a representação de cadeia de caracteres do deslocamento de fuso horário local do usuário em elementos de matriz separada.  
  
10. Chame o <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> ou <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=nameWithType> método para converter a data e hora da solicitação do usuário para um <xref:System.DateTime> valor. Use uma sobrecarga do método com um `provider` parâmetro e passe a ele um dos seguintes:  
  
    -   O <xref:System.Globalization.CultureInfo> objeto criado na etapa 8.  
  
    -   O <xref:System.Globalization.DateTimeFormatInfo> objeto que é retornado pelo <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> propriedade o <xref:System.Globalization.CultureInfo> objeto criado na etapa 8.  
  
11. Se a operação de análise na etapa 10 falhar, vá para a etapa 13. Caso contrário, chame o <xref:System.UInt32.Parse%28System.String%29?displayProperty=nameWithType> método para converter a representação de cadeia de caracteres do deslocamento de fuso horário do usuário para um número inteiro.  
  
12. Criar uma instância de um <xref:System.DateTimeOffset> que representa a hora local do usuário chamando o <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=nameWithType> construtor.  
  
13. Se a conversão na etapa 10 falhar, repita as etapas 7 a 12 para cada elemento restante na matriz de cadeia de caracteres retornadas pelo <xref:System.Web.HttpRequest.UserLanguages%2A> propriedade.  
  
14. Se a conversão ainda falhar ou se a matriz de cadeia de caracteres retornada pelo <xref:System.Web.HttpRequest.UserLanguages%2A> propriedade estiver vazia, analise a cadeia de caracteres usando a cultura invariável, que é retornado pelo <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> propriedade. Em seguida, repita as etapas 7 a 12.  
  
 O resultado é um <xref:System.DateTimeOffset> objeto que representa a hora local do usuário da página da Web. Em seguida, você pode determinar o UTC equivalente chamando o <xref:System.DateTimeOffset.ToUniversalTime%2A> método. Você também pode determinar a data e hora equivalentes no seu servidor Web chamando o <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> método e passando um valor de <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> como o fuso horário de hora será convertida.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir contém o código-fonte HTML e o código para um formulário da Web do ASP.NET que pede ao usuário para um valor de data e hora de entrada. Um script do lado do cliente também grava informações sobre o local data e hora da solicitação do usuário e o deslocamento de fuso horário do usuário do UTC em um campo oculto. Em seguida, essa informação é analisada pelo servidor, que retorna uma página da Web que exibe a entrada do usuário. Ele também exibe a data e hora da solicitação do usuário usando a hora local do usuário, a hora no servidor e o UTC.  
  
 [!code-aspx-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]
 [!code-aspx-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]
  
 O script do lado do cliente chama o JavaScript `toLocaleString` método. Isso produz uma cadeia de caracteres que segue as convenções de formatação da localidade do usuário, que é mais provável a ser analisado com sucesso no servidor.  
  
 O <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> propriedade é preenchida com os nomes de cultura que estão contidos em `Accept-Language` cabeçalhos incluídos em uma solicitação HTTP. No entanto, nem todos os navegadores incluem `Accept-Language` cabeçalhos em suas solicitações e os usuários também podem suprimir os cabeçalhos totalmente. Isso torna importante ter uma cultura de fallback ao analisar a entrada do usuário. Normalmente, a cultura de fallback é a cultura invariável retornada por <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Os usuários também podem fornecer Internet Explorer com nomes de cultura que sua entrada em uma caixa de texto, que cria a possibilidade de que os nomes de cultura podem não ser válidos. Isso torna importante usar tratamento de exceções ao instanciar um <xref:System.Globalization.CultureInfo> objeto.  
  
 Quando recuperados de uma solicitação HTTP enviada pelo Internet Explorer, o <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> matriz é preenchida por ordem de preferência do usuário. O primeiro elemento na matriz contém o nome da cultura/região primária do usuário. Se a matriz contém quaisquer itens adicionais, Internet Explorer arbitrariamente atribui a eles um especificador de qualidade, que é delimitado do nome da cultura por um ponto e vírgula. Por exemplo, uma entrada para a cultura fr-FR pode tomar a forma `fr-FR;q=0.7`.  
  
 O exemplo chama o <xref:System.Globalization.CultureInfo.%23ctor%2A> construtor com seu `useUserOverride` parâmetro definido como `false` para criar um novo <xref:System.Globalization.CultureInfo> objeto. Isso garante que, se o nome de cultura é o nome de cultura padrão no servidor, o novo <xref:System.Globalization.CultureInfo> criado pelo construtor de classe de objeto contém as configurações padrão de uma cultura e não reflete quaisquer configurações substituídas usando o servidor  **Regional e opções de idioma** aplicativo. Os valores de quaisquer configurações substituídas no servidor são provavelmente não existem no sistema do usuário ou sejam refletidas na entrada do usuário.  
  
 Como este exemplo analisa duas representações de cadeia de caracteres de data e hora (uma entrada pelo usuário, a outra armazenada para o campo oculto), ele define os possíveis <xref:System.Globalization.CultureInfo> objetos que podem ser necessários com antecedência. Ele cria uma matriz de <xref:System.Globalization.CultureInfo> objetos que é maior do que o número de elementos retornados pelo <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> propriedade. Ele instancia um <xref:System.Globalization.CultureInfo> de objeto para cada cadeia de caracteres de linguagem/região e também instancia um <xref:System.Globalization.CultureInfo> objeto que representa <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
 Seu código pode chamar tanto o <xref:System.DateTime.Parse%2A> ou <xref:System.DateTime.TryParse%2A> método para converter a representação de cadeia de caracteres do usuário de uma data e hora para um <xref:System.DateTime> valor. Chamadas repetidas para um método de análise podem ser necessárias para uma única operação de análise. Como resultado, o <xref:System.DateTime.TryParse%2A> método é melhor porque retorna `false` se uma operação de análise falhar. Por outro lado, manipular as exceções repetidas que podem ser geradas pelo <xref:System.DateTime.Parse%2A> método pode ser uma proposta muito cara em um aplicativo Web.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Para compilar o código, crie um [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] página da Web sem um código oculto. Copie o exemplo para a página da Web para que ele substitui todo o código existente. O [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] página da Web deve conter os seguintes controles:  
  
-   Um <xref:System.Web.UI.WebControls.Label> controle, que não é referenciado no código. Definir seu <xref:System.Web.UI.WebControls.TextBox.Text%2A> propriedade como "digite um número:".  
  
-   Um <xref:System.Web.UI.WebControls.TextBox> controle chamado `DateString`.  
  
-   Um <xref:System.Web.UI.WebControls.Button> controle chamado `OKButton`. Definir seu <xref:System.Web.UI.WebControls.Button.Text%2A> propriedade como "Okey".  
  
-   Um <xref:System.Web.UI.WebControls.HiddenField> controle chamado `DateInfo`.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Para impedir que um usuário insira script no fluxo de HTML, entrada do usuário deve nunca ser ecoada diretamente de volta na resposta do servidor. Em vez disso, ela deve ser codificada usando o <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> método.  
  
## <a name="see-also"></a>Consulte também  
 [Executando operações de formatação](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Cadeias de caracteres de formato de data e hora padrão](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [Cadeias de caracteres de formato de data e hora personalizado](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
 [Analisando cadeias de caracteres de data e hora](../../../docs/standard/base-types/parsing-datetime.md)
