---
title: Como imprimir arquivos XPS de forma programática
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing XPS files programmatically [WPF]
- XPS files [WPF], printing programmatically
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
ms.openlocfilehash: cc86a7e7c6a816af37c3d063825ed62583afa78a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966992"
---
# <a name="how-to-programmatically-print-xps-files"></a>Como imprimir arquivos XPS de forma programática

Você pode usar uma sobrecarga do método <xref:System.Printing.PrintQueue.AddJob%2A> para imprimir arquivos XPS (XML Paper Specification) sem abrir um <xref:System.Windows.Controls.PrintDialog> ou, em princípio, qualquer [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].

Você também pode imprimir arquivos XPS usando os vários métodos de <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A?displayProperty=nameWithType> e <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A?displayProperty=nameWithType>. Para obter mais informações, consulte [imprimindo um documento XPS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90)).

Outra maneira de imprimir XPS é usar os métodos <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A?displayProperty=nameWithType> ou <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A?displayProperty=nameWithType>. Consulte [Invocar uma caixa de diálogo Imprimir](how-to-invoke-a-print-dialog.md).

## <a name="example"></a>Exemplo

As principais etapas para usar o método de <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> de três parâmetros são as seguintes. O exemplo abaixo fornece detalhes.

1. Determine se a impressora é uma impressora XPSDrv. Consulte [visão geral de impressão](printing-overview.md) para saber mais sobre XPSDrv.

2. Se a impressora não for uma impressora XPSDrv, defina o apartment do thread como um thread único.

3. Crie uma instância de um servidor de impressão e um objeto de fila de impressão.

4. Chame o método, especificando um nome de trabalho, o arquivo a ser impresso e um <xref:System.Boolean> sinalizador indicando se a impressora é uma impressora XPSDrv ou não.

O exemplo a seguir mostra como imprimir em lote todos os arquivos XPS em um diretório. Embora o aplicativo solicite ao usuário que especifique o diretório, o método de <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> de três parâmetros não requer um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Ele pode ser usado em qualquer caminho de código em que você tenha um nome de arquivo XPS e um caminho que você possa passar para ele.

A sobrecarga de <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> de três parâmetros de <xref:System.Printing.PrintQueue.AddJob%2A> deve ser executada em um único thread apartment sempre que o parâmetro <xref:System.Boolean> for `false`, que deve ser quando uma impressora não XPSDrv estiver sendo usada. No entanto, o estado de apartment padrão para .NET é um thread múltiplo. Esse padrão deve ser revertido, uma vez que o exemplo supõe uma impressora não XPSDrv.

Há duas maneiras de alterar o padrão. Uma maneira é simplesmente adicionar o <xref:System.STAThreadAttribute> (ou seja, "`[System.STAThreadAttribute()]`") logo acima da primeira linha do método de `Main` do aplicativo (geralmente "`static void Main(string[] args)`"). No entanto, muitos aplicativos exigem que o método `Main` tenha um estado apartment multi-threaded, portanto, há um segundo método: Coloque a chamada para <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> em um thread separado cujo estado apartment esteja definido como <xref:System.Threading.ApartmentState.STA> com <xref:System.Threading.Thread.SetApartmentState%2A>. O exemplo a seguir usa essa segunda técnica.

Da mesma forma, o exemplo começa instanciando um objeto <xref:System.Threading.Thread> e passando-o um método **PrintXPS** como o parâmetro <xref:System.Threading.ThreadStart>. (O método **PrintXPS** é definido posteriormente no exemplo.) Em seguida, o thread é definido como um single thread apartment. O único código restante do método `Main` inicia o novo thread.

A parte principal do exemplo está no exemplo `static` **BatchXPSPrinter.PrintXPS**. Depois de criar um servidor de impressão e uma fila, o método solicita ao usuário um diretório que contém arquivos XPS. Depois de validar a existência do diretório e a presença de arquivos \*. XPS nele, o método adiciona cada arquivo à fila de impressão. O exemplo supõe que a impressora não é XPSDrv, portanto, estamos passando `false` para o último parâmetro do método <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>. Por esse motivo, o método validará a marcação XPS no arquivo antes de tentar convertê-lo para a linguagem de descrição de página da impressora. Se a validação falhar, uma exceção será lançada. O código de exemplo detectará a exceção, notificará o usuário sobre ele e, em seguida, passará para processar o próximo arquivo XPS.

[!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
[!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]

Se estiver usando uma impressora XPSDrv, você poderá definir o parâmetro final como `true`. Nesse caso, como XPS é a linguagem de descrição de página da impressora, o método enviará o arquivo para a impressora sem validá-lo ou convertê-lo em outra linguagem de descrição de página. Se você não tiver certeza em tempo de design se o aplicativo usará uma impressora XPSDrv, poderá modificar o aplicativo para que ele leia a propriedade <xref:System.Printing.PrintQueue.IsXpsDevice%2A> e Branch de acordo com o que encontrar.

Como inicialmente, algumas impressoras XPSDrv estarão disponíveis imediatamente após o lançamento do Windows Vista e do Microsoft .NET Framework, talvez seja necessário disfarçar uma impressora não XPSDrv como uma impressora XPSDrv. Para fazer isso, adicione Pipelineconfig.xml à lista de arquivos na seguinte chave do Registro do computador que executa o aplicativo:

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\ *\<PseudoXPSPrinter>* \DependentFiles

em que *\<PseudoXPSPrinter>* é qualquer fila de impressão. O computador, então, deve ser reinicializado.

Esse disfarce permitirá que você passe `true` como o parâmetro final de <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> sem causar uma exceção, mas como *\<PseudoXPSPrinter >* não é realmente uma impressora XPSDrv, somente o lixo será impresso.

> [!NOTE]
> Para simplificar, o exemplo acima usa a presença de uma extensão \*. XPS como seu teste de que um arquivo é XPS. No entanto, os arquivos XPS não precisam ter essa extensão. O [isXPS. exe (ferramenta de conformidade do isXPS)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100)) é uma maneira de testar um arquivo para a validade do XPS.

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
