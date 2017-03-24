---
title: "Constantes e enumerações (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- enumerations [Visual Basic]
- constants
- constants, list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e37ef2e3c51e96e85cb214054195016e69d52382
ms.lasthandoff: 03/13/2017

---
# <a name="constants-and-enumerations-visual-basic"></a>Constantes e enumerações (Visual Basic)
[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Fornece um número de enumerações e constantes predefinidas para desenvolvedores. Constantes armazenam valores que permanecem constantes durante a execução de um aplicativo. Enumerações fornecem uma maneira conveniente para trabalhar com conjuntos de constantes relacionadas e para associar valores constantes com nomes.  
  
## <a name="constants"></a>Constantes  
  
### <a name="conditional-compilation-constants"></a>Constantes de Compilação Condicional  
 A tabela a seguir lista as constantes predefinidas disponíveis para compilação condicional.  
  
|**Constante**|**Descrição**|  
|---|---|  
|`CONFIG`|Uma cadeia de caracteres que corresponde à configuração atual do **configuração da solução ativa** caixa de **do Configuration Manager**.|  
|`DEBUG`|A `Boolean` valor que pode ser definida no **propriedades do projeto** caixa de diálogo. Por padrão, a configuração de depuração para um projeto define `DEBUG`. Quando `DEBUG` for definida, <xref:System.Diagnostics.Debug>métodos da classe geram saída para o **saída** janela.</xref:System.Diagnostics.Debug> Quando não estiver definido, <xref:System.Diagnostics.Debug>métodos de classe não são compilados e nenhuma saída de depuração será gerada.</xref:System.Diagnostics.Debug>|  
|`TARGET`|Uma cadeia de caracteres que representa o tipo de saída para o projeto ou a configuração da linha de comando **/destino** opção. Os valores possíveis de `TARGET` são:<br /><br /> -"winexe" para um aplicativo do Windows.<br />-"exe" para um aplicativo de console.<br />-"library" para uma biblioteca de classes.<br />-"module" para um módulo.<br />-Os **/destino** opção pode ser definida no [!INCLUDE[vsprvs](../../csharp/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado. Para obter mais informações, consulte [/target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`TRACE`|A `Boolean` valor que pode ser definida no **propriedades do projeto** caixa de diálogo. Por padrão, todas as configurações para um projeto definem `TRACE`. Quando `TRACE` for definida, <xref:System.Diagnostics.Trace>métodos da classe geram saída para o **saída** janela.</xref:System.Diagnostics.Trace> Quando não estiver definido, <xref:System.Diagnostics.Trace>classe métodos não são compilados e nenhuma `Trace` saída é gerada.</xref:System.Diagnostics.Trace>|  
|`VBC_VER`|Um número que representa o [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] versão, na *principais*.* pequenas* formato. O número de versão [!INCLUDE[vbprvblong](../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] é 8.0.|  
  
### <a name="print-and-display-constants"></a>Imprimir e exibir constantes  
 Quando você chama impressão e exibe as funções, você pode usar as seguintes constantes em seu código no lugar dos valores reais.  
  
|**Constante**|**Descrição**|  
|---|---|  
|`vbCrLf`|Combinação de caracteres de retorno/alimentação de linha de carro.|  
|`vbCr`|Caractere de retorno de carro.|  
|`vbLf`|Caractere de avanço de linha.|  
|`vbNewLine`|Caractere de nova linha.|  
|`vbNullChar`|Caractere nulo.|  
|`vbNullString`|Não é igual de uma cadeia de caracteres de comprimento zero (""); usado para chamar procedimentos externos.|  
|`vbObjectError`|Número do erro. Os números de erro definidos pelo usuário devem ser maiores que esse valor. Por exemplo:<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|Caractere de tabulação.|  
|`vbBack`|Caractere de BACKSPACE.|  
|`vbFormFeed`|Não usado no Microsoft Windows.|  
|`vbVerticalTab`|Não é útil no Microsoft Windows.|  
  
## <a name="enumerations"></a>Enumerações  
 A tabela a seguir lista e descreve enumerações fornecidas por [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
|Enumeração|Descrição|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle></xref:Microsoft.VisualBasic.AppWinStyle>|Indica o estilo da janela para usar para o programa invocado quando chama o <xref:Microsoft.VisualBasic.Interaction.Shell%2A>função.</xref:Microsoft.VisualBasic.Interaction.Shell%2A>|  
|<xref:Microsoft.VisualBasic.AudioPlayMode></xref:Microsoft.VisualBasic.AudioPlayMode>|Indica como tocar sons ao chamar métodos de áudio.|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole></xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|Indica o tipo de função para checar ao chamar o <xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>método.</xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>|  
|<xref:Microsoft.VisualBasic.CallType></xref:Microsoft.VisualBasic.CallType>|Indica o tipo de procedimento que está sendo invocado quando se chama o <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>função.</xref:Microsoft.VisualBasic.Interaction.CallByName%2A>|  
|<xref:Microsoft.VisualBasic.CompareMethod></xref:Microsoft.VisualBasic.CompareMethod>|Indica como comparar cadeias de caracteres ao chamar funções de comparação.|  
|<xref:Microsoft.VisualBasic.DateFormat></xref:Microsoft.VisualBasic.DateFormat>|Indica como exibir datas quando se chama o <xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>função.</xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|  
|<xref:Microsoft.VisualBasic.DateInterval></xref:Microsoft.VisualBasic.DateInterval>|Indica como determinar e formatar intervalos de datas ao chamar funções relacionadas a datas.|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption></xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|Especifica o que deve ser feito quando um diretório que deve ser excluído contém arquivos ou diretórios.|  
|<xref:Microsoft.VisualBasic.DueDate></xref:Microsoft.VisualBasic.DueDate>|Indica quando os pagamentos vencem ao chamar métodos financeiros.|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType></xref:Microsoft.VisualBasic.FileIO.FieldType>|Indica se os campos de texto são delimitados ou largura fixa.|  
|<xref:Microsoft.VisualBasic.FileAttribute></xref:Microsoft.VisualBasic.FileAttribute>|Indica os atributos de arquivo a usar ao chamar funções de acesso a arquivos.|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek></xref:Microsoft.VisualBasic.FirstDayOfWeek>|Indica o primeiro dia da semana a ser usado ao chamar funções relacionadas a datas.|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear></xref:Microsoft.VisualBasic.FirstWeekOfYear>|Indica a primeira semana do ano a ser usada ao chamar funções relacionadas a datas.|  
|<xref:Microsoft.VisualBasic.MsgBoxResult></xref:Microsoft.VisualBasic.MsgBoxResult>|Indica qual botão foi pressionado na caixa de mensagem, retornada pelo <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>função.</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle></xref:Microsoft.VisualBasic.MsgBoxStyle>|Indica quais botões Exibir quando se chama o <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>função.</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>|  
|<xref:Microsoft.VisualBasic.OpenAccess></xref:Microsoft.VisualBasic.OpenAccess>|Indica como abrir um arquivo ao chamar funções de acesso a arquivos.|  
|<xref:Microsoft.VisualBasic.OpenMode></xref:Microsoft.VisualBasic.OpenMode>|Indica como abrir um arquivo ao chamar funções de acesso a arquivos.|  
|<xref:Microsoft.VisualBasic.OpenShare></xref:Microsoft.VisualBasic.OpenShare>|Indica como abrir um arquivo ao chamar funções de acesso a arquivos.|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption></xref:Microsoft.VisualBasic.FileIO.RecycleOption>|Especifica se um arquivo deve ser excluído permanentemente ou colocado na Lixeira.|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption></xref:Microsoft.VisualBasic.FileIO.SearchOption>|Especifica se deve pesquisar todos ou somente diretórios de alto nível.|  
|<xref:Microsoft.VisualBasic.TriState></xref:Microsoft.VisualBasic.TriState>|Indica uma `Boolean` valor ou se o padrão deve ser usado ao chamar funções de formatação numérica.|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption></xref:Microsoft.VisualBasic.FileIO.UICancelOption>|Especifica o que deve ser feito se o usuário clicar em **Cancelar** durante uma operação.|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption></xref:Microsoft.VisualBasic.FileIO.UIOption>|Especifica se deseja ou não mostrar uma caixa de diálogo de progresso quando copiar, excluir ou mover arquivos ou diretórios.|  
|<xref:Microsoft.VisualBasic.VariantType></xref:Microsoft.VisualBasic.VariantType>|Indica o tipo de um objeto variante, retornado pelo <xref:Microsoft.VisualBasic.Information.VarType%2A>função.</xref:Microsoft.VisualBasic.Information.VarType%2A>|  
|<xref:Microsoft.VisualBasic.VbStrConv></xref:Microsoft.VisualBasic.VbStrConv>|Indica qual tipo de conversão a ser executada ao chamar o <xref:Microsoft.VisualBasic.Strings.StrConv%2A>função.</xref:Microsoft.VisualBasic.Strings.StrConv%2A>|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de linguagem do Visual Basic](../../visual-basic/language-reference/index.md)   
 [Visual Basic](../../visual-basic/index.md)   
 [Visão geral de constantes](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Visão geral de Enumerações](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
