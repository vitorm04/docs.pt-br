---
title: 'Como: Imprimir arquivos XPS com programação'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing XPS files programmatically [WPF]
- XPS files [WPF], printing programmatically
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
ms.openlocfilehash: 28197b22b379b84c34e7fdf8991472e082c8cb42
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855749"
---
# <a name="how-to-programmatically-print-xps-files"></a>Como: Imprimir arquivos XPS com programação

Você pode usar uma sobrecarga do <xref:System.Printing.PrintQueue.AddJob%2A> método para imprimir arquivos XPS (XML Paper Specification) sem abrir um <xref:System.Windows.Controls.PrintDialog> ou, em princípio, qualquer um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] .

Você também pode imprimir arquivos XPS usando os muitos <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A?displayProperty=nameWithType> métodos <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A?displayProperty=nameWithType> e. Para obter mais informações, consulte [imprimindo um documento XPS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90)).

Outra maneira de imprimir o XPS é usar os <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A?displayProperty=nameWithType> métodos <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A?displayProperty=nameWithType> ou. Consulte [Invocar uma caixa de diálogo Imprimir](how-to-invoke-a-print-dialog.md).

## <a name="example"></a>Exemplo

As principais etapas para usar o método de três <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> parâmetros são as seguintes. O exemplo abaixo fornece detalhes.

1. Determine se a impressora é uma impressora XPSDrv. (Consulte [Visão geral de impressão](printing-overview.md) para obter mais informações sobre XPSDrv.)

2. Se a impressora não for uma impressora XPSDrv, defina o apartment do thread como um thread único.

3. Crie uma instância de um servidor de impressão e um objeto de fila de impressão.

4. Chame o método, especificando um nome de trabalho, o arquivo a ser impresso e um <xref:System.Boolean> sinalizador que indica se a impressora é ou não uma impressora XPSDrv.

O exemplo a seguir mostra como imprimir em lote todos os arquivos XPS em um diretório. Embora o aplicativo solicite ao usuário que especifique o diretório, o método de três <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> parâmetros não requer um. [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Ele pode ser usado em qualquer caminho de código em que você tenha um nome de arquivo XPS e um caminho que você possa passar para ele.

A sobrecarga de três <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> parâmetros de <xref:System.Printing.PrintQueue.AddJob%2A> deve ser executada em um único thread apartment sempre <xref:System.Boolean> que o `false`parâmetro é, que deve ser quando uma impressora não XPSDrv está sendo usada. No entanto, o estado de apartment padrão para .NET é um thread múltiplo. Esse padrão deve ser revertido, uma vez que o exemplo supõe uma impressora não XPSDrv.

Há duas maneiras de alterar o padrão. Uma delas é <xref:System.STAThreadAttribute> simplesmente adicionar o (ou seja, "`[System.STAThreadAttribute()]`") logo acima da primeira linha do método do `Main` aplicativo (normalmente "`static void Main(string[] args)`"). No entanto, muitos aplicativos exigem `Main` que o método tenha um estado apartment multi-threaded, portanto, há um segundo método: colocar a <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> chamada em em um thread separado cujo estado de apartamento está definido como <xref:System.Threading.ApartmentState.STA> with <xref:System.Threading.Thread.SetApartmentState%2A>. O exemplo a seguir usa essa segunda técnica.

De acordo, o exemplo começa instanciando um <xref:System.Threading.Thread> objeto e passando-o um método **PrintXPS** como <xref:System.Threading.ThreadStart> o parâmetro. (O método **PrintXPS** é definido posteriormente no exemplo.) Em seguida, o thread é definido como um apartment de thread único. O único código restante do método `Main` inicia o novo thread.

A parte principal do exemplo está no exemplo `static` **BatchXPSPrinter.PrintXPS**. Depois de criar um servidor de impressão e uma fila, o método solicita ao usuário um diretório que contém arquivos XPS. Depois de validar a existência do diretório e a presença de \*arquivos. XPS nele, o método adiciona cada arquivo à fila de impressão. O exemplo supõe que a impressora não é XPSDrv, portanto, estamos passando `false` para o último parâmetro do <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> método. Por esse motivo, o método validará a marcação XPS no arquivo antes de tentar convertê-lo para a linguagem de descrição de página da impressora. Se a validação falhar, uma exceção será lançada. O código de exemplo detectará a exceção, notificará o usuário sobre ele e, em seguida, passará para processar o próximo arquivo XPS.

[!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
[!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]

Se estiver usando uma impressora XPSDrv, você poderá definir o parâmetro final como `true`. Nesse caso, como XPS é a linguagem de descrição de página da impressora, o método enviará o arquivo para a impressora sem validá-lo ou convertê-lo em outra linguagem de descrição de página. Se você não tiver certeza em tempo de design se o aplicativo usará uma impressora XPSDrv, poderá modificar o aplicativo para que ele leia a <xref:System.Printing.PrintQueue.IsXpsDevice%2A> Propriedade e a ramificação de acordo com o que encontrar.

Como inicialmente, algumas impressoras XPSDrv estarão disponíveis imediatamente após o lançamento do [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] e Microsoft .NET Framework, talvez seja necessário disfarçar uma impressora não XPSDrv como uma impressora XPSDrv. Para fazer isso, adicione Pipelineconfig.xml à lista de arquivos na seguinte chave do Registro do computador que executa o aplicativo:

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\ *\<PseudoXPSPrinter>* \DependentFiles

em que *\<PseudoXPSPrinter>* é qualquer fila de impressão. O computador, então, deve ser reinicializado.

Esse disfarce permitirá que você passe `true` como o parâmetro final de <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> sem causar uma exceção, mas como  *\<PseudoXPSPrinter >* não é realmente uma impressora XPSDrv, somente o lixo será impresso.

> [!NOTE]
> Para simplificar, o exemplo acima usa a presença de \*uma extensão. XPS como seu teste de que um arquivo é XPS. No entanto, os arquivos XPS não precisam ter essa extensão. O [isXPS. exe (ferramenta de conformidade do isXPS)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100)) é uma maneira de testar um arquivo para a validade do XPS.

## <a name="see-also"></a>Consulte também

- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.AddJob%2A>
- <xref:System.Threading.ApartmentState>
- <xref:System.STAThreadAttribute>
- [Documentos XPS](/windows/desktop/printdocs/documents)
- [Imprimindo um documento XPS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90))
- [Threads gerenciados e não gerenciados](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))
- [isXPS. exe (ferramenta de conformidade do isXPS)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100))
- [Documentos no WPF](documents-in-wpf.md)
- [Visão Geral da Impressão](printing-overview.md)
