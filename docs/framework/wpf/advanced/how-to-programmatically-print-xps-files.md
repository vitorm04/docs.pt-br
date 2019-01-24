---
title: 'Como: Imprimir arquivos XPS de forma programática'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing XPS files programmatically [WPF]
- XPS files [WPF], printing programmatically
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
ms.openlocfilehash: fbef6aef11917a4e8f0a098c523ec2b542664681
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556607"
---
# <a name="how-to-programmatically-print-xps-files"></a>Como: Imprimir arquivos XPS de forma programática
Você pode usar uma sobrecarga da <xref:System.Printing.PrintQueue.AddJob%2A> método para imprimir [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] arquivos sem abrir uma <xref:System.Windows.Controls.PrintDialog> ou, em princípio, qualquer [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] em todos os.  
  
 Você também pode imprimir [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] de arquivos usando muitos <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> e <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> métodos do <xref:System.Windows.Xps.XpsDocumentWriter>. Para saber mais sobre isso, consulte [Imprimindo um documento XPS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90)).  
  
 Outra maneira de impressão [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] é usar o <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> ou <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A> métodos do <xref:System.Windows.Controls.PrintDialog> controle. Consulte [Invocar uma caixa de diálogo Imprimir](how-to-invoke-a-print-dialog.md).  
  
## <a name="example"></a>Exemplo  
 As etapas principais para usar o parâmetro de três <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> método são da seguinte maneira. O exemplo abaixo fornece detalhes.  
  
1.  Determine se a impressora é uma impressora XPSDrv. (Consulte [Visão geral de impressão](printing-overview.md) para obter mais informações sobre XPSDrv.)  
  
2.  Se a impressora não for uma impressora XPSDrv, defina o apartment do thread como um thread único.  
  
3.  Crie uma instância de um servidor de impressão e um objeto de fila de impressão.  
  
4.  Chame o método, especificando um nome de trabalho, o arquivo a ser impresso e um <xref:System.Boolean> sinalizador que indica se a impressora é uma impressora XPSDrv ou não.  
  
 O exemplo a seguir mostra como imprimir em lote todos os arquivos [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] em um diretório. Embora o aplicativo solicite ao usuário especificar o diretório, o parâmetro de três <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> método não requer um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Ele pode ser usado em qualquer caminho de código em que você tem um nome de arquivo [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] e um caminho que pode passar para ele.  
  
 O parâmetro de três <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> sobrecarga do <xref:System.Printing.PrintQueue.AddJob%2A> deve ser executado em um único thread apartment sempre que o <xref:System.Boolean> parâmetro é `false`, que deve ser quando uma impressora não XPSDrv estiver sendo usada. No entanto, o estado de apartment padrão para [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] é de vários threads. Esse padrão deve ser revertido, uma vez que o exemplo supõe uma impressora não XPSDrv.  
  
 Há duas maneiras de alterar o padrão. Uma maneira é simplesmente adicionar o <xref:System.STAThreadAttribute> (ou seja, "`[System.STAThreadAttribute()]`") logo acima a primeira linha da caixa de diálogo `Main` método (geralmente "`static void Main(string[] args)`"). No entanto, muitos aplicativos exigem que o `Main` método têm um estado de apartment com multithread, portanto, não há um segundo método: colocar a chamada para <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> em um thread separado cujo estado de apartment é definido como <xref:System.Threading.ApartmentState.STA> com <xref:System.Threading.Thread.SetApartmentState%2A>. O exemplo a seguir usa essa segunda técnica.  
  
 Da mesma forma, o exemplo começa criando uma instância de um <xref:System.Threading.Thread> objeto e passá-lo um **PrintXPS** método como o <xref:System.Threading.ThreadStart> parâmetro. (O método **PrintXPS** é definido posteriormente no exemplo.) Em seguida, o thread é definido como um apartment de thread único. O único código restante do método `Main` inicia o novo thread.  
  
 A parte principal do exemplo está no exemplo `static` **BatchXPSPrinter.PrintXPS**. Após criar um servidor e uma fila de impressão, o método solicita ao usuário um diretório que contém arquivos [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]. Após validar a existência do diretório e a presença de \*de arquivos. xps nele, o método adiciona cada arquivo à fila de impressão. O exemplo supõe que a impressora é não-XPSDrv, portanto, estamos passando `false` para o último parâmetro da <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> método. Por esse motivo, o método validará a marcação [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] no arquivo antes de tentar convertê-lo na linguagem de descrição de página da impressora. Se a validação falhar, uma exceção será lançada. O código de exemplo capturará a exceção, notificará o usuário sobre ela e, em seguida, processará o arquivo [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] seguinte.  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 Se estiver usando uma impressora XPSDrv, você poderá definir o parâmetro final como `true`. Nesse caso, como [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] é a linguagem de descrição de página da impressora, o método enviará o arquivo para a impressora sem validá-lo ou convertê-lo para outra linguagem de descrição de página. Se não souber em tempo de design se o aplicativo usará uma impressora XPSDrv, você pode modificar o aplicativo para que ele leia o <xref:System.Printing.PrintQueue.IsXpsDevice%2A> propriedade e a ramificação de acordo com o que encontrar.  
  
 Como inicialmente haverá poucas impressoras XPSDrv disponíveis logo após o lançamento do [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] e Microsoft .NET Framework, você talvez precise disfarçar uma impressora não XPSDrv como uma impressora XPSDrv. Para fazer isso, adicione Pipelineconfig.xml à lista de arquivos na seguinte chave do Registro do computador que executa o aplicativo:  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\*\<PseudoXPSPrinter>* \DependentFiles  
  
 em que *\<PseudoXPSPrinter>* é qualquer fila de impressão. O computador, então, deve ser reinicializado.  
  
 Este disfarce permitirá que você passe `true` como o parâmetro final de <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> sem causar uma exceção, mas como  *\<PseudoXPSPrinter >* não é realmente uma impressora XPSDrv, somente lixo será impresso.  
  
 **Observação** para simplificar, o exemplo acima usa a presença de um \*a extensão. XPS como seu teste de um arquivo é [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]. No entanto, arquivos [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] não precisam ter essa extensão. O [isXPS.exe (ferramenta de conformidade isXPS)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100)) é uma maneira de testar a validade [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] de um arquivo.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.AddJob%2A>
- <xref:System.Threading.ApartmentState>
- <xref:System.STAThreadAttribute>
- [XPS](https://www.microsoft.com/xps)
- [Imprimindo um documento XPS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90))
- [Threading gerenciado e não gerenciado](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))
- [isXPS.exe (conformidade isXPS)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100))
- [Documentos no WPF](documents-in-wpf.md)
- [Visão Geral da Impressão](printing-overview.md)
