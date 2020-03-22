---
title: Usar expressões regulares com o controle MaskedTextBox
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: b997f6f495fca51e888bb995fee0361d29d68048
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148278"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Usando expressões regulares com o controle MaskedTextBox no Visual Basic
Este exemplo demonstra como converter expressões regulares simples para trabalhar com o <xref:System.Windows.Forms.MaskedTextBox> controle.  
  
## <a name="description-of-the-masking-language"></a>Descrição da Linguagem de Mascaramento  
 A <xref:System.Windows.Forms.MaskedTextBox> linguagem de mascaramento padrão é `Masked Edit` baseada na usada pelo controle no Visual Basic 6.0 e deve ser familiar para os usuários que migram dessa plataforma.  
  
 A <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriedade <xref:System.Windows.Forms.MaskedTextBox> do controle especifica qual máscara de entrada usar. A máscara deve ser uma corda composta por um ou mais dos elementos mascarados da tabela a seguir.  
  
|Elemento mascarado|Descrição|Elemento de expressão regular|  
|---------------------|-----------------|--------------------------------|  
|0|Qualquer dígito entre 0 e 9. Entrada necessária.|\d|  
|9|Dígito ou espaço. Entrada opcional.|[\d]?|  
|#|Dígito ou espaço. Entrada opcional. Se esta posição for deixada em branco na máscara, ela será renderizada como um espaço. Mais (+) e menos (-) sinais são permitidos.|[ \d+-]?|  
|L|Carta ASCII. Entrada necessária.|[a-zA-Z]|  
|?|Carta ASCII. Entrada opcional.|[a-zA-Z]?|  
|&|Caractere. Entrada necessária.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|Caractere. Entrada opcional.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|Um|Alfanumérico. Entrada opcional.|\W|  
|.|Espaço reservado decimal apropriado para a cultura.|Não disponível.|  
|,|Espaço reservado para a cultura.|Não disponível.|  
|:|Separador de tempo apropriado para a cultura.|Não disponível.|  
|/|Separador de datas apropriado para a cultura.|Não disponível.|  
|$|Símbolo de moeda apropriado para a cultura.|Não disponível.|  
|\<|Converte todos os caracteres que seguem para minúsculas.|Não disponível.|  
|>|Converte todos os caracteres que seguem para maiúsculas.|Não disponível.|  
|&#124;|Desfaz um turno anterior para cima ou para baixo.|Não disponível.|  
|&#92;|Escapa de um personagem de máscara, transformando-o em um literal. "\\\\é a seqüência de fuga para uma barra invertida.|&#92;|  
|Todos os outros personagens.|Literais Todos os elementos não-máscara <xref:System.Windows.Forms.MaskedTextBox>aparecerão como eles mesmos dentro .|Todos os outros personagens.|  
  
 Os símbolos decimal (.), milésimos (,), tempo (:), data (/) e moeda ($) padrão para exibir esses símbolos conforme definido pela cultura do aplicativo. Você pode forçá-los a exibir símbolos para outra cultura usando a <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> propriedade.  
  
## <a name="regular-expressions-and-masks"></a>Expressões e máscaras regulares  
 Embora você possa usar expressões e máscaras regulares para validar a entrada do usuário, elas não são completamente equivalentes. Expressões regulares podem expressar padrões mais complexos do que máscaras, mas máscaras podem expressar as mesmas informações de forma mais sucinta e em um formato culturalmente relevante.  
  
 A tabela a seguir compara quatro expressões regulares e a máscara equivalente para cada uma.  
  
|Expressão regular|Mask|Observações|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|O `/` caractere na máscara é um separador de datas lógico, e aparecerá para o usuário como o separador de data apropriado para a cultura atual do aplicativo.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Uma data (dia, mês abreviação e ano) no formato dos Estados Unidos em que a abreviação de três letras é exibida com uma letra maiúscula inicial seguida de duas letras minúsculas.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|Número de telefone dos Estados Unidos, código de área opcional. Se o usuário não desejar inserir os caracteres opcionais, ele pode entrar em espaços ou colocar o ponteiro do mouse diretamente na posição na máscara representada pelo primeiro 0.|  
|`$\d{6}.00`|`$999,999.00`|Um valor monetário na faixa de 0 a 999999. A moeda, caracteres milésimos e decimais serão substituídos em tempo de execução por seus equivalentes específicos da cultura.|  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [Validando cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
- [Controle MaskedTextBox](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)
