---
title: "Práticas recomendadas para o desenvolvimento de aplicativos prontos para internacionalização"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- global applications, best practices
- world-ready applications, best practices
- globalization [.NET Framework], best practices
- international applications [.NET Framework], best practices
ms.assetid: f08169c7-aad8-4ec3-9a21-9ebd3b89986c
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8a50080fa4b84abe84fbb1a44f18e1fb680a07c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="best-practices-for-developing-world-ready-applications"></a>Práticas recomendadas para o desenvolvimento de aplicativos prontos para internacionalização
Esta seção descreve as práticas recomendadas a seguir ao desenvolver aplicativos prontos para o mundo.  
  
## <a name="globalization-best-practices"></a>Práticas recomendadas de globalização  
  
1.  Torne o aplicativo Unicode internamente.  
  
2.  Use as classes com reconhecimento de cultura fornecidas pelo <xref:System.Globalization> namespace manipular e formatar dados.  
  
    -   Para classificar, usar o <xref:System.Globalization.SortKey> classe e o <xref:System.Globalization.CompareInfo> classe.  
  
    -   Para comparações de cadeia de caracteres, use o <xref:System.Globalization.CompareInfo> classe.  
  
    -   Para formatação de data e hora, use o <xref:System.Globalization.DateTimeFormatInfo> classe.  
  
    -   Para formatação numérica, use o <xref:System.Globalization.NumberFormatInfo> classe.  
  
    -   Para calendários gregoriano e não gregorianos, use o <xref:System.Globalization.Calendar> classe ou uma das implementações de calendário específico.  
  
3.  Use as configurações de propriedade da cultura fornecidas pelo <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> classe nas situações apropriadas. Use o <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> tarefas de propriedade de formatação, como a data e hora ou formatação numérica. Use o <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> propriedade para recuperar os recursos. Observe que o `CurrentCulture` e `CurrentUICulture` propriedades podem ser definidas por thread.  
  
4.  Habilitar seu aplicativo para ler e gravar dados em uma variedade de codificações usando as classes de codificação no <xref:System.Text> namespace. Não suponha dados ASCII. Suponha que os caracteres internacionais serão fornecidos em qualquer lugar, um usuário pode inserir texto. Por exemplo, o aplicativo deve aceitar caracteres internacionais em nomes de servidor, diretórios, nomes de arquivos, nomes de usuário e URLs.  
  
5.  Ao usar o <xref:System.Text.UTF8Encoding> classe, por motivos de segurança, use o recurso de detecção de erro oferecido por essa classe. Para ativar o recurso de detecção de erro, o aplicativo cria uma instância da classe usando o construtor que assume um `throwOnInvalidBytes` parâmetro e define o valor desse parâmetro para `true`.  
  
6.  Sempre que possível, identificador de cadeias de caracteres como cadeias de caracteres inteiras em vez de como uma série de caracteres individuais. Isso é especialmente importante durante a classificação ou procurando subcadeias de caracteres. Isso evitará problemas associados à análise caracteres combinados.  
  
7.  Exibir o texto usando as classes fornecidas pelo <xref:System.Drawing> namespace.  
  
8.  Para obter consistência entre sistemas operacionais, não permitem que as configurações de usuário substituir <xref:System.Globalization.CultureInfo>. Use o `CultureInfo` construtor que aceite um `useUserOverride` parâmetro e defini-lo como `false`.  
  
9. Teste a funcionalidade de seu aplicativo em versões de sistemas operacionais internacionais, usando dados internacionais.  
  
10. Se uma decisão de segurança é baseada no resultado de uma comparação de cadeia de caracteres ou operação de alteração de caso, ter o aplicativo executar uma operação de cultura. Essa prática garante que o resultado não é afetado pelo valor de `CultureInfo.CurrentCulture`. Consulte a seção "Cadeia de caracteres comparações que Use a cultura atual" [práticas recomendadas para usar cadeias de caracteres](../../../docs/standard/base-types/best-practices-strings.md) para obter um exemplo que demonstra a cadeia de caracteres como sensíveis à cultura comparações podem produzir resultados inconsistentes.  
  
## <a name="localization-best-practices"></a>Práticas recomendadas de localização  
  
1.  Mova todos os recursos localizáveis para separar DLLs somente de recursos. Recursos localizáveis incluem elementos de interface do usuário, como cadeias de caracteres, mensagens de erro, caixas de diálogo, menus e recursos do objeto inserido.  
  
2.  Fazer não codificar cadeias de caracteres ou recursos de interface do usuário.  
  
3.  Não coloque recursos nonlocalizable as DLLs somente de recursos. Isso causa confusão para os tradutores.  
  
4.  Não não use composto cadeias de caracteres que são criadas em tempo de execução de frases concatenados. Cadeias de caracteres compostas são difíceis de localizar porque geralmente assumem uma ordem gramatical em inglês que não se aplicam a todos os idiomas.  
  
5.  Evite construções ambíguas, como "Pasta vazia" onde as cadeias de caracteres podem ser convertidas diferente dependendo das funções gramaticais dos componentes de cadeia de caracteres. Por exemplo, "vazio" pode ser um verbo ou um adjetivo, que pode levar a diferentes traduções em linguagens como italiano ou francês.  
  
6.  Evite usar imagens e ícones que contêm texto em seu aplicativo. Eles são caros de localizar.  
  
7.  Permitir espaço suficiente para o comprimento de cadeias de caracteres para expandir na interface do usuário. Em alguns idiomas, frases podem exigir 50 a 75% mais espaço do que eles precisam de outras linguagens.  
  
8.  Use o <xref:System.Resources.ResourceManager?displayProperty=nameWithType> classe para recuperar os recursos com base na cultura.  
  
9. Usar o Visual Studio para criar caixas de diálogo de formulários do Windows, para que eles podem ser localizados usando o [Editor de recursos do Windows Forms (Winres.exe)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md). Não codificar caixas de diálogo de Windows Forms manualmente.  
  
10. Organize professional localização (tradução).  
  
11. Para obter uma descrição completa de criação e a localização de recursos, consulte [recursos em aplicativos](../../../docs/framework/resources/index.md).  
  
## <a name="globalization-best-practices-for-aspnet-applications"></a>Práticas recomendadas de globalização para aplicativos ASP.NET  
  
1.  Definir explicitamente o <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> e <xref:System.Globalization.CultureInfo.CurrentCulture%2A> propriedades em seu aplicativo. Não confie em padrões.  
  
2.  Observe que os aplicativos ASP.NET são aplicativos gerenciados e, portanto, podem usar as mesmas classes como outros aplicativos gerenciados para recuperar, exibir e manipular informações com base na cultura.  
  
3.  Lembre-se de que você pode especificar os seguintes três tipos de codificações no ASP.NET:  
  
    -   requestEncoding Especifica a codificação recebida do navegador do cliente.  
  
    -   responseEncoding Especifica a codificação para enviar para o navegador do cliente. Na maioria das situações, essa codificação deve ser o mesmo que o especificado para requestEncoding.  
  
    -   fileEncoding Especifica a codificação padrão para. aspx,. asmx e. asax ao analisar o arquivo.  
  
4.  Especifique os valores para os atributos requestEncoding responseEncoding, fileEncoding, cultura e uiCulture nos seguintes três locais em um aplicativo ASP.NET:  
  
    -   Na seção de globalização de um arquivo Web. config. Esse arquivo é externo ao aplicativo ASP.NET. Para obter mais informações, consulte [ \<globalização > elemento](http://msdn.microsoft.com/en-us/e2dffc8e-ebd2-439b-a2fd-e3ac5e620da7).  
  
    -   Em uma diretiva de página. Observe que, quando um aplicativo está em uma página, o arquivo já foi lido. Portanto, é muito tarde para especificar fileEncoding e requestEncoding. Somente uiCulture, cultura e responseEncoding podem ser especificados em uma diretiva de página.  
  
    -   Programaticamente no código do aplicativo. Essa configuração pode variar por solicitação. Com uma diretiva de página, quando o código do aplicativo é atingido ele é muito tarde para especificar fileEncoding e requestEncoding. Somente uiCulture, cultura e responseEncoding podem ser especificados no código do aplicativo.  
  
5.  Observe que o valor de uiCulture pode ser definido para o navegador idioma aceito.  
  
## <a name="see-also"></a>Consulte também  
 [Globalização e localização](../../../docs/standard/globalization-localization/index.md)  
 [Recursos em aplicativos de área de trabalho](../../../docs/framework/resources/index.md)
