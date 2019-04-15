---
title: 'Como: Exibir informações localizadas de data e hora para usuários da Web'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- formatting [.NET Framework], dates
- parsing strings [.NET Framework], date and time strings
- localization [.NET Framework], date and time displays
- formatting [.NET Framework], localized data
- displaying date and time data
- localized date displays [.NET Framework]
ms.assetid: 377fe93c-32be-421a-a30a-be639a46ede8
dev_langs:
- csharp
- vb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e97bc095332e626d79561ab5fdc7bad531e3ba31
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320152"
---
# <a name="how-to-display-localized-date-and-time-information-to-web-users"></a>Como: Exibir informações localizadas de data e hora para usuários da Web
Como uma página da Web pode ser exibida em qualquer lugar no mundo, operações que analisam e formatam valores de data e hora não devem depender de um formato padrão (que geralmente é o formato da cultura local do servidor Web) ao interagir com o usuário. Em vez disso, formulários da Web que lidam com cadeias de caracteres de data e hora inseridas pelo usuário devem analisar as cadeias de caracteres usando a cultura preferencial do usuário. Da mesma forma, os dados de data e hora devem ser exibidos para o usuário em um formato compatível com a respectiva cultura. Este tópico mostra como fazer isso.  
  
## <a name="to-parse-date-and-time-strings-input-by-the-user"></a>Para analisar a data e a hora em cadeias de caracteres de entrada do usuário  
  
1. Determine se a matriz de cadeia de caracteres retornada pela propriedade <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> é populada. Se não for, vá para a etapa 6.  
  
2. Se a matriz de cadeia de caracteres retornada pela propriedade <xref:System.Web.HttpRequest.UserLanguages%2A> for populada, recupere o primeiro elemento. O primeiro elemento indica o idioma e a região padrão ou preferenciais do usuário.  
  
3. Crie uma instância de um objeto <xref:System.Globalization.CultureInfo> que represente a cultura preferencial do usuário do chamando o construtor <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>.  
  
4. Chame o método `TryParse` ou o `Parse` do tipo <xref:System.DateTime> ou <xref:System.DateTimeOffset> para tentar a conversão. Use uma sobrecarga do método `TryParse` ou `Parse` com um parâmetro `provider` e passe para ele um dos seguintes itens:  
  
    -   O objeto <xref:System.Globalization.CultureInfo> criado na etapa 3.  
  
    -   O objeto <xref:System.Globalization.DateTimeFormatInfo> que é retornado pela propriedade <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> do objeto <xref:System.Globalization.CultureInfo> criado na etapa 3.  
  
5. Se a conversão falhar, repita as etapas 2 a 4 para cada elemento restante na matriz de cadeia de caracteres retornada pela propriedade <xref:System.Web.HttpRequest.UserLanguages%2A>.  
  
6. Se a conversão ainda falhar ou se a matriz de cadeia de caracteres retornada pela propriedade <xref:System.Web.HttpRequest.UserLanguages%2A> estiver vazia, analise a cadeia de caracteres usando a cultura invariável, que é retornada pela propriedade <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
## <a name="to-parse-the-local-date-and-time-of-the-users-request"></a>Para analisar a data e a hora local da solicitação do usuário  
  
1. Adicione um controle <xref:System.Web.UI.WebControls.HiddenField> a um formulário da Web.  
  
2. Crie uma função JavaScript que manipula o eventos `onClick` de um botão `Submit` gravando a data e a hora atuais e o deslocamento do fuso horário local do UTC (Tempo Universal Coordenado) para a propriedade <xref:System.Web.UI.WebControls.HiddenField.Value%2A>. Use um delimitador (como ponto e vírgula) para separar os dois componentes da cadeia de caracteres.  
  
3. Use o evento <xref:System.Web.UI.Control.PreRender> do formulário de Web para injetar a função no fluxo de saída de HTML, passando o texto do script para o método <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>.  
  
4. Conecte o manipulador de eventos ao evento `onClick` do botão `Submit`, fornecendo o nome da função JavaScript ao atributo `OnClientClick` do botão `Submit`.  
  
5. Crie um manipulador para o evento <xref:System.Web.UI.WebControls.Button.Click> do botão `Submit`.  
  
6. No manipulador de eventos, determine se a matriz de cadeia de caracteres retornada pela propriedade <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> é populada. Se não for, vá para a etapa 14.  
  
7. Se a matriz de cadeia de caracteres retornada pela propriedade <xref:System.Web.HttpRequest.UserLanguages%2A> for populada, recupere o primeiro elemento. O primeiro elemento indica o idioma e a região padrão ou preferenciais do usuário.  
  
8. Crie uma instância de um objeto <xref:System.Globalization.CultureInfo> que represente a cultura preferencial do usuário do chamando o construtor <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>.  
  
9. Passe a cadeia de caracteres atribuída à propriedade <xref:System.Web.UI.WebControls.HiddenField.Value%2A> para o método <xref:System.String.Split%2A> para armazenar a representação de cadeia de caracteres de data local do usuário e a representação de cadeia de caracteres do deslocamento de fuso horário local do usuário em elementos de matriz separada.  
  
10. Chame o método <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> ou <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=nameWithType> para converter a data e a hora da solicitação do usuário em um valor <xref:System.DateTime>. Use uma sobrecarga do método com um parâmetro `provider` e passe a ele um dos seguintes itens:  
  
    -   O objeto <xref:System.Globalization.CultureInfo> criado na etapa 8.  
  
    -   O objeto <xref:System.Globalization.DateTimeFormatInfo> que é retornado pela propriedade <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> do objeto <xref:System.Globalization.CultureInfo> criado na etapa 8.  
  
11. Se a operação de análise na etapa 10 falhar, vá para a etapa 13. Caso contrário, chame o método <xref:System.UInt32.Parse%28System.String%29?displayProperty=nameWithType> para converter a representação de cadeia de caracteres do deslocamento de fuso horário do usuário em um número inteiro.  
  
12. Crie uma instância de <xref:System.DateTimeOffset> que represente a hora local do usuário chamando o construtor <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=nameWithType>.  
  
13. Se a conversão na etapa 10 falhar, repita as etapas 7 a 12 para cada elemento restante na matriz de cadeia de caracteres retornada pela propriedade <xref:System.Web.HttpRequest.UserLanguages%2A>.  
  
14. Se a conversão ainda falhar ou se a matriz de cadeia de caracteres retornada pela propriedade <xref:System.Web.HttpRequest.UserLanguages%2A> estiver vazia, analise a cadeia de caracteres usando a cultura invariável, que é retornada pela propriedade <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Repita as etapas de 7 a 12.  
  
 O resultado é um objeto <xref:System.DateTimeOffset> que representa a hora local do usuário da página da Web. Em seguida, você pode determinar o UTC equivalente chamando o método <xref:System.DateTimeOffset.ToUniversalTime%2A>. Você também pode determinar a data e hora equivalentes no servidor Web chamando o método <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> e passando um valor <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> como o fuso horário para converter a hora.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir contém o código-fonte HTML e o código para um formulário da Web do ASP.NET que pede ao usuário um valor de data e hora de entrada. Um script do lado do cliente também grava informações sobre o local data e a hora da solicitação do usuário e o deslocamento de fuso horário do usuário de UTC em um campo oculto. Em seguida, essas informações são analisadas pelo servidor, que retorna uma página da Web que exibe a entrada do usuário. Também exibe a data e hora da solicitação do usuário usando a hora local do usuário, a hora no servidor e UTC.  
  
 [!code-aspx-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]
 [!code-aspx-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]
  
 O script do lado do cliente chama o método JavaScript `toLocaleString`. Isso produz uma cadeia de caracteres que segue as convenções de formatação da localidade do usuário, que tem maior probabilidade de ser analisada com êxito no servidor.  
  
 A propriedade <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> é populada com os nomes de cultura que estão contidos em cabeçalhos `Accept-Language` incluídos em uma solicitação HTTP. No entanto, nem todos os navegadores incluem cabeçalhos `Accept-Language` em suas solicitações, e os usuários também podem suprimir totalmente os cabeçalhos. Por isso, é importante ter uma cultura de fallback ao analisar a entrada do usuário. Normalmente, a cultura de fallback é a cultura invariável retornada por <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Os usuários também podem fornecer ao Internet Explorer nomes de cultura que inserem em uma caixa de texto, o que cria a possibilidade de que os nomes de cultura não sejam válidos. Assim, é importante usar o tratamento de exceções ao instanciar um objeto <xref:System.Globalization.CultureInfo>.  
  
 Quando recuperada de uma solicitação HTTP enviada pelo Internet Explorer, a matriz <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> é populada por ordem de preferência do usuário. O primeiro elemento na matriz contém o nome da cultura/região principal do usuário. Se a matriz contiver itens adicionais, o Internet Explorer atribuirá arbitrariamente a eles um especificador de qualidade, que é delimitado do nome da cultura por um ponto e vírgula. Por exemplo, uma entrada para a cultura fr-FR pode ter o formato `fr-FR;q=0.7`.  
  
 O exemplo chama o construtor <xref:System.Globalization.CultureInfo.%23ctor%2A> com o parâmetro `useUserOverride` definido como `false` para criar um novo objeto <xref:System.Globalization.CultureInfo>. Isso garante que, se o nome de cultura for o nome de cultura padrão no servidor, o novo <xref:System.Globalization.CultureInfo> criado pelo construtor de classe de objeto conterá as configurações padrão de uma cultura e não refletirá configurações substituídas usando o aplicativo **Opções Regionais e de Idioma** do servidor. Os valores de configurações substituídas no servidor provavelmente não existem no sistema do usuário nem são refletidos na entrada do usuário.  
  
 Como este exemplo analisa duas representações de cadeia de caracteres de data e hora (uma entrada do usuário e outra armazenada para o campo oculto), ele define os possíveis objetos <xref:System.Globalization.CultureInfo> que podem ser necessários com antecedência. Ele cria uma matriz de objetos <xref:System.Globalization.CultureInfo> que é maior do que o número de elementos retornados pela propriedade <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>. Ele instancia um objeto <xref:System.Globalization.CultureInfo> para cada cadeia de caracteres de idioma/região e também instancia um objeto <xref:System.Globalization.CultureInfo> que representa <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
 O código pode chamar o método <xref:System.DateTime.Parse%2A> ou <xref:System.DateTime.TryParse%2A> para converter a representação de cadeia de caracteres do usuário de uma data e hora em um valor <xref:System.DateTime>. As chamadas repetidas para um método de análise podem ser necessárias para uma única operação de análise. Como resultado, o método <xref:System.DateTime.TryParse%2A> é melhor porque retorna `false` se uma operação de análise falha. Por outro lado, manipular as exceções repetidas que podem ser geradas pelo método <xref:System.DateTime.Parse%2A> pode ser uma proposta muito cara em um aplicativo Web.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Para compilar o código, crie uma página da Web [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sem code-behind. Copie o exemplo para a página da Web para que ele substitua todo o código existente. A página da Web [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] deve conter os seguintes controles:  
  
-   Um controle <xref:System.Web.UI.WebControls.Label>, que não é referenciado no código. Defina a propriedade <xref:System.Web.UI.WebControls.TextBox.Text%2A> como "Digite um Número:".  
  
-   Um controle <xref:System.Web.UI.WebControls.TextBox> chamado `DateString`.  
  
-   Um controle <xref:System.Web.UI.WebControls.Button> chamado `OKButton`. Defina sua propriedade <xref:System.Web.UI.WebControls.Button.Text%2A> como "OK".  
  
-   Um controle <xref:System.Web.UI.WebControls.HiddenField> chamado `DateInfo`.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Para impedir que um usuário insira script no fluxo de HTML, a entrada do usuário nunca deve ser ecoada diretamente de volta na resposta do servidor. Em vez disso, ela deve ser codificada usando o método <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- [Executando operações de formatação](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Cadeias de caracteres de formato de data e hora padrão](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Cadeias de caracteres de formato de data e hora personalizado](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [Analisar cadeias de caracteres de Data e Hora](../../../docs/standard/base-types/parsing-datetime.md)
