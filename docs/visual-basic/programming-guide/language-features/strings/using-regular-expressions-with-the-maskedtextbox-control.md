---
title: Usar expressões regulares com o controle MaskedTextBox
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: 12d500fa0ff4945dcf2d5009bdba6d337834707e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346259"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Usando expressões regulares com o controle MaskedTextBox no Visual Basic
Este exemplo demonstra como converter expressões regulares simples para trabalhar com o controle <xref:System.Windows.Forms.MaskedTextBox>.  
  
## <a name="description-of-the-masking-language"></a>Descrição da linguagem de mascaramento  
 A linguagem de mascaramento de <xref:System.Windows.Forms.MaskedTextBox> padrão é baseada na usada pelo controle de `Masked Edit` no Visual Basic 6,0 e deve ser familiar aos usuários que estão migrando dessa plataforma.  
  
 A propriedade <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> do controle de <xref:System.Windows.Forms.MaskedTextBox> especifica qual máscara de entrada usar. A máscara deve ser uma cadeia de caracteres composta de um ou mais elementos de mascaramento da tabela a seguir.  
  
|Elemento de mascaramento|Descrição|Elemento de expressão regular|  
|---------------------|-----------------|--------------------------------|  
|0|Qualquer dígito único entre 0 e 9. Entrada necessária.|\d|  
|9|Dígito ou espaço. Entrada opcional.|[ \d]?|  
|#|Dígito ou espaço. Entrada opcional. Se essa posição for deixada em branco na máscara, ela será renderizada como um espaço. São permitidos sinais de mais (+) e de menos (-).|[ \d+-]?|  
|L|Letra ASCII. Entrada necessária.|[a-zA-Z]|  
|?|Letra ASCII. Entrada opcional.|[a-zA-Z]?|  
|&|Caractere. Entrada necessária.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|Caractere. Entrada opcional.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|A|Alfanumérico. Entrada opcional.|\W|  
|.|Espaço reservado decimal adequado à cultura.|Não disponível.|  
|,|Espaço reservado para milhares apropriados de cultura.|Não disponível.|  
|:|Separador de tempo adequado à cultura.|Não disponível.|  
|/|Separador de data adequado à cultura.|Não disponível.|  
|$|Símbolo de moeda apropriado para a cultura.|Não disponível.|  
|\<|Converte todos os caracteres que seguem para minúsculas.|Não disponível.|  
|>|Converte todos os caracteres que seguem para letras maiúsculas.|Não disponível.|  
|&#124;|Desfaz um deslocamento anterior ou deslocado para baixo.|Não disponível.|  
|&#92;|Escapa um caractere de máscara, transformando-o em um literal. "\\\\" é a sequência de escape para uma barra invertida.|&#92;|  
|Todos os outros caracteres.|Literais. Todos os elementos sem máscara aparecerão como eles mesmos dentro <xref:System.Windows.Forms.MaskedTextBox>.|Todos os outros caracteres.|  
  
 Os símbolos decimal (.), milésimos (,), tempo (:), data (/) e moeda ($) são padrão para exibir esses símbolos, conforme definido pela cultura do aplicativo. Você pode forçá-los a Exibir símbolos para outra cultura usando a propriedade <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>.  
  
## <a name="regular-expressions-and-masks"></a>Expressões regulares e máscaras  
 Embora você possa usar expressões regulares e máscaras para validar a entrada do usuário, elas não são completamente equivalentes. As expressões regulares podem expressar padrões mais complexos do que as máscaras, mas as máscaras podem expressar as mesmas informações de forma mais sucinta e em um formato culturalmente relevante.  
  
 A tabela a seguir compara quatro expressões regulares e a máscara equivalente para cada uma.  
  
|Expressão Regular|Máscara|{1&gt;Observações&lt;1}|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|O `/` caractere na máscara é um separador de data lógico e aparecerá para o usuário como o separador de data apropriado para a cultura atual do aplicativo.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Uma data (dia, mês abreviação e ano) no formato Estados Unidos no qual a abreviação de mês de três letras é exibida com uma letra maiúscula inicial seguida por duas letras minúsculas.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|Número de telefone Estados Unidos, código de área opcional. Se o usuário não quiser inserir os caracteres opcionais, ele poderá inserir espaços ou colocar o ponteiro do mouse diretamente na posição na máscara representada pelo primeiro 0.|  
|`$\d{6}.00`|`$999,999.00`|Um valor de moeda no intervalo de 0 a 999999. A moeda, os milésimos e os caracteres decimais serão substituídos em tempo de execução com seus equivalentes específicos à cultura.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [Validando cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
- [Controle MaskedTextBox](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)
