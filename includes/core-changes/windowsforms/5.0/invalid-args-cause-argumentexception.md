---
ms.openlocfilehash: aab7d8538c875e35c832acc2a6c64beb84d4fb47
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702423"
---
### <a name="winforms-methods-now-throw-argumentexception"></a>Os métodos WinForms agora lançam ArgumentException

Alguns métodos de Windows Forms agora lançam um <xref:System.ArgumentException> para argumentos inválidos, onde anteriormente não fizeram isso.

#### <a name="change-description"></a>Descrição da alteração

Anteriormente, passar argumentos de um tipo inesperado ou incorreto para determinados métodos de Windows Forms resultaria em um estado indeterminado. A partir do .NET 5,0, esses métodos agora geram um <xref:System.ArgumentException> quando passaram argumentos inválidos.

Lançar um <xref:System.ArgumentException> está em conformidade com o comportamento do tempo de execução do .net. Ele também melhora a experiência de depuração ao comunicar-se claramente qual argumento é inválido.

A tabela a seguir lista os métodos e parâmetros afetados:

| Método | Nome do parâmetro | Condição | Versão adicionada |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | O argumento não é do tipo <xref:System.Windows.Forms.TabPage> . | 5,0 visualização 1 |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | Argumento é `null` , <xref:System.String.Empty?displayProperty=nameWithType> ou espaço em branco. | 5,0 Preview 5 |

#### <a name="version-introduced"></a>Versão introduzida

.NET 5,0

#### <a name="recommended-action"></a>Ação recomendada

- Atualize o código para evitar a passagem de argumentos inválidos.
- Se necessário, manipule um <xref:System.ArgumentException> ao chamar o método.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>
- <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`

-->
