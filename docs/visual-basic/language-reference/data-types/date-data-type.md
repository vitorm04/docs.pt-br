---
title: "Tipo de dados Data (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Date"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "especificador # para literais de data"
  - "tipos de dados [Visual Basic], atribuindo"
  - "valores de dados"
  - "tipo de dados de data"
  - "Literais de data"
  - "datas, tipo de dados de data"
  - "datas, tipos de dados do Visual Basic"
  - "literais, Data"
  - "horas, tipo de dados de data"
  - "horas, tipos de dados do Visual Basic"
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de dados Data (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Contém valores de \(8 bytes\) IEEE de 64 bits que representam desde 1 de janeiro do ano de 0001 até 31 de dezembro de 9999 ano de datas e horas de 12:00:00 AM \(meia\-noite\) por meio de 11:59:59.9999999 PM.  Cada incremento representa 100 nanossegundos de tempo decorrido desde o início de 1º de janeiro do ano 1 no calendário gregoriano.  O valor máximo representa 100 nanossegundos antes do início de 1º de janeiro do ano 10000.  
  
## Comentários  
 Use o `Date` tipo de dados para conter valores de data, os valores de hora ou valores de data e hora.  
  
 O valor padrão de `Date` é 0:00:00 \(meia\-noite\) em 1º de janeiro de 0001.  
  
 Você pode obter a data atual e a hora do <xref:Microsoft.VisualBasic.DateAndTime> classe.  
  
## Requisitos de formato  
 Você deve colocar um `Date` literal entre sinais numéricos \(`# #`\).  Você deve especificar o valor de data no formato dd\/aaaa, por exemplo `#5/31/1993#`, ou AAAA\-MM\-dd, por exemplo `#1993-5-31#`.  Você pode usar barras ao especificar o ano pela primeira vez.  Esse requisito é independente da sua localidade e data do seu computador e as configurações de formato de hora.  
  
 A razão para essa restrição é que o significado de seu código nunca deve alterar dependendo da localidade na qual o aplicativo é executado.  Suponha que você codifique uma `Date` literal de `#3/4/1998#` e pretender dizer 4 de março de 1998.  Em uma localidade que utilize dd\/mm\/aaaa, 4\/3\/1998 compila como você deseja.  Mas suponha que você implantar seu aplicativo em muitos países.  Uma localidade que utilize mm\/dd\/aaaa, seria compilar o literal embutido para 3 de abril de 1998.  Em uma localidade que utilize aaaa\/mm\/dd, o literal seria inválido \(abril de 1998, 0003\) e causa um erro do compilador.  
  
## Soluções alternativas  
 Para converter um `Date` literal no formato de sua localidade, ou em um formato personalizado, forneça o literal para o <xref:Microsoft.VisualBasic.Strings.Format%2A> função, especificando um formato de data predefinidos ou definidos pelo usuário.  O exemplo a seguir demonstra isso.  
  
```  
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))  
```  
  
 Como alternativa, você pode usar um dos construtores sobrecarregados do <xref:System.DateTime> estrutura para montar um valor de data e hora.  O exemplo a seguir cria um valor para representar a 31 de maio de 1993 em 12:14 à tarde.  
  
```  
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)   
```  
  
## Formato de hora  
 Você pode especificar o valor de hora no formato de 12 horas ou 24 horas, por exemplo `#1:15:30 PM#` ou `#13:15:30#`.  No entanto, se você não especificar os minutos ou segundos, você deve especificar AM ou PM.  
  
## Data e hora padrão  
 Se você não incluir uma data em uma literal de data\/hora, o Visual Basic define a parte de data do valor 1 de janeiro, 0001.  Se você não incluir uma vez em um literal de data\/hora, o Visual Basic define a parte de hora do valor para o início do dia, ou seja, meia\-noite \(0:00\).  
  
## Conversões de tipo  
 Se você converter um `Date` valor o `String` do tipo, Visual Basic apresenta a data de acordo com o formato de data abreviada especificado pela localidade do tempo de execução e ele processa a hora de acordo com o formato de hora \(12 horas ou 24 horas\) especificada pela localidade do tempo de execução.  
  
## Dicas de programação  
  
-   **Considerações de interoperabilidade.** Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos Automation ou COM, tenha em mente que tipos em outros ambientes de data\/hora não são compatíveis com o Visual Basic `Date` tipo.  Se você estiver passando um argumento de data\/hora para esse componente, declare\-o como `Double` em vez de `Date` no seu novo Visual Basic code e usar os métodos de conversão <xref:System.DateTime.FromOADate%2A?displayProperty=fullName> e <xref:System.DateTime.ToOADate%2A?displayProperty=fullName>.  
  
-   **Digite caracteres.** `Date` não tem nenhum caractere de tipo literal ou um caractere de tipo identificador.  No entanto, o compilador trata literais entre sinais numéricos \(`# #`\) como `Date`.  
  
-   **Tipos de framework.** O tipo correspondente no .NET Framework é a estrutura <xref:System.DateTime?displayProperty=fullName>.  
  
## Exemplo  
 Uma variável ou constante do `Date` tipo de dados contém a data e a hora.  O exemplo a seguir ilustra essa situação.  
  
```  
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#  
```  
  
## Consulte também  
 <xref:System.DateTime?displayProperty=fullName>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Cadeias de caracteres de formato de data e hora padrão](../Topic/Standard%20Date%20and%20Time%20Format%20Strings.md)   
 [Cadeias de caracteres de formato de data e hora personalizado](../Topic/Custom%20Date%20and%20Time%20Format%20Strings.md)   
 [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)