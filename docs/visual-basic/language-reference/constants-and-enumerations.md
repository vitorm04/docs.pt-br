---
title: "Constantes e enumera&#231;&#245;es (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "constantes"
  - "constantes, lista de"
  - "enumerações [Visual Basic]"
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Constantes e enumera&#231;&#245;es (Visual Basic)
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece um número de enumerações e constantes predefinidas para desenvolvedores.  Constantes armazenam valores que permanecem constantes durante a execução de um aplicativo.  Enumerações fornecem uma maneira conveniente para trabalhar com conjuntos de constantes relacionadas e para associar valores constantes com nomes.  
  
## Constantes  
  
### Constantes de compilação condicional  
 As seguinte tabela lista as constantes predefinadas disponível para compilação condicional.  
  
|||  
|-|-|  
|**Constante**|**Descrição**|  
|`CONFIG`|Uma string correponde à atual configuração da caixa **Configuração de Solução Ativa** no  **Gerenciador de Configuração**.|  
|`DEBUG`|O valor `Boolean` pode ser definido na caixa de diálogo **Propriedades do Projeto**.  Por padrão, a configuração de Debug para um projeto define `DEBUG`.  Quando `DEBUG` é definido, os métodos da classe <xref:System.Diagnostics.Debug> geram saída para a janela de **Saída**.  Quando isso não é definido, métodos da classe <xref:System.Diagnostics.Debug> não são compilados e nenhuma saída de Debug é gerada.|  
|`TARGET`|Uma string representando o tipo de saída para o projeto ou a configuração da opção da linha de comanhdo **\/target**.  Os valores possíveis de `TARGET` são:<br /><br /> -   "winexe" para um aplicativo do Windows.<br />-   "exe" para um aplicativo de console.<br />-   "biblioteca" para uma biblioteca de classes.<br />-   "módulo" para um módulo.<br />-   O **\/target** opção pode ser definida na [!INCLUDE[vsprvs](../../csharp/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado.  Para obter mais informações, consulte [\/target](../../visual-basic/reference/command-line-compiler/target.md).|  
|`TRACE`|O valor `Boolean` pode ser definido na caixa de diálogo **Propriedades do Projeto**.  Por padrão, todas configuração para um projeto define `TRACE`.  Quando `TRACE` é definido, os métodos da classe <xref:System.Diagnostics.Trace> geram saída para a janela de **Saída**.  Quando isso não é definido, métodos da classe <xref:System.Diagnostics.Trace> não são compilados e nenhuma saída `Trace` é gerada.|  
|`VBC_VER`|Um número que representa o [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] versão, na  *principais*. *secundária* formato.  O número de versão [!INCLUDE[vbprvblong](../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] é a 8.0.|  
  
### Imprimir e Exibir Constantes  
 Quando você chamar funções de impressão e exibição, você pode usar as seguintes constantes em seu código no lugar dos valores reais.  
  
|||  
|-|-|  
|**Constante**|**Descrição**|  
|`vbCrLf`|Combinação de caracteres de retorno\/alimentação de linha de carro.|  
|`vbCr`|Caractere de retorno de carro.|  
|`vbLf`|Caractere de alimentação de linha|  
|`vbNewLine`|Caractere de nova linha.|  
|`vbNullChar`|Caractere nulo.|  
|`vbNullString`|Diferente de uma sequência de caracteres de comprimento nulo \(""\); usado para chamar procedimentos externos.|  
|`vbObjectError`|Número de Erro  Números de erro definidos pelo usuário devem ser maiores que esse valor.  Por exemplo:<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|Caractere de tabulação.|  
|`vbBack`|Caractere de backspace.|  
|`vbFormFeed`|Não é usado no Microsoft Windows.|  
|`vbVerticalTab`|Não é útil no Microsoft Windows.|  
  
## Enumerações  
 A tabela a seguir lista e descreve enumerações fornecidas por [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
|||  
|-|-|  
|Enumeração|Descrição|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|Indica o estilo de janela para se usar para o programa invocado quando chama a função <xref:Microsoft.VisualBasic.Interaction.Shell%2A>.|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|Indica como tocar sons quando se chamam os métodos de áudio.|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|Indica o tipo de função para verificar quando chamar o <xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A> método.|  
|<xref:Microsoft.VisualBasic.CallType>|Indica o tipo de procedimento que está sendo invocado quando se chama a função <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>.|  
|<xref:Microsoft.VisualBasic.CompareMethod>|Indica como comparar sequencia de caracteres quando se chamam funções de comparação.|  
|<xref:Microsoft.VisualBasic.DateFormat>|Indica como exibir datas quando se chama a função <xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>.|  
|<xref:Microsoft.VisualBasic.DateInterval>|Indica como determinar e formatar intervalos de data quando se chamam funções de datas relacionadas.|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|Especifica o que deve ser feito quando um diretório que está para ser excluído contém arquivos ou diretórios.|  
|<xref:Microsoft.VisualBasic.DueDate>|Indica quando pagamentos estão previstos quando se chamam métodos financeiros.|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|Indica se campos de texto são delimitados ou de largura fixa.|  
|<xref:Microsoft.VisualBasic.FileAttribute>|Indica os atributos de arquivo a usar quando se chamam funções de acesso de arquivo.|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|Indica o primeiro dia da semana a se usar quando se chamam funções de datas relacionadas.|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|Indica o primeiro dia do ano a se usar quando se chamam funções de datas relacionadas.|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|Indica qual botão foi pressionado na caixa de mensagem, retornada pela função <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>.|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|Indica quais botões exibir quando se chama a função <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>.|  
|<xref:Microsoft.VisualBasic.OpenAccess>|Indica como abrir um arquivo ao chamar funções de acesso a arquivos.|  
|<xref:Microsoft.VisualBasic.OpenMode>|Indica como abrir um arquivo ao chamar funções de acesso a arquivos.|  
|<xref:Microsoft.VisualBasic.OpenShare>|Indica como abrir um arquivo ao chamar funções de acesso a arquivos.|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|Especifica se um arquivo deve ser excluído permanentemente ou colocado na Lixeira.|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|Especifica se deve\-se procurar todos ou somente diretórios de alto nível.|  
|<xref:Microsoft.VisualBasic.TriState>|Indica um valor `Boolean` ou se o padrão deve ser usado quando chamar funções de formatação de números.|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|Especifica o que deve ser feito se o usuário clica **Cancelar** durante uma operação.|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|Especifica se mostrar ou não uma caixa de diálogo de progresso quando se copia, exclui ou se move arquivos ou diretórios.|  
|<xref:Microsoft.VisualBasic.VariantType>|Indica o tipo de um objeto variante, retornado pela função <xref:Microsoft.VisualBasic.Information.VarType%2A>.|  
|<xref:Microsoft.VisualBasic.VbStrConv>|Indica qual tipo de conversão realizar quando se chama a função <xref:Microsoft.VisualBasic.Strings.StrConv%2A>.|  
  
## Consulte também  
 [Referência da linguagem Visual Basic](../../visual-basic/language-reference/index.md)   
 [Visual Basic](../../visual-basic/index.md)   
 [Visão geral de constantes](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Visão geral de enumerações](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)