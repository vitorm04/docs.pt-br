---
title: Modelo de threading
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text on buttons [WPF], updating
- message processing [WPF], nested
- blocking operations [WPF]
- Common Language Runtime (CLR), locking mechanism
- locking mechanism of Common Language Runtime (CLR)
- threading model [WPF]
- Word [WPF], spelling checking
- button text [WPF], updating
- spelling checking in Word [WPF]
- asynchronous behavior [WPF], exposing
- nested message processing [WPF]
- reentrancy [WPF]
ms.assetid: 02d8fd00-8d7c-4604-874c-58e40786770b
ms.openlocfilehash: 0bcb0e7369345aaae39d99a005a07304aaad7043
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200344"
---
# <a name="threading-model"></a>Modelo de threading
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] foi projetado para livrar os desenvolvedores das dificuldades de threading. Como resultado, a maioria dos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] os desenvolvedores não terão que escrever uma interface que usa mais de um thread. Como os programas multi-threaded são complexos e difíceis de serem depurados, deve-se evitá-los quando existem soluções single-threaded.  
  
 Não importa quão bem projetada, no entanto, não [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] estrutura nunca será capaz de fornecer uma solução single-threaded para todos os tipos de problema. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] chega perto, mas ainda existem situações em que vários threads melhora [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] desempenho e capacidade de resposta dos aplicativos. Depois de abordar alguns documentos de suporte, este artigo explora algumas dessas situações e, em seguida, termina com uma discussão de alguns detalhes de nível mais baixo.  

> [!NOTE]
>  Este tópico discute o threading usando o <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> método para chamadas assíncronas. Você também pode fazer chamadas assíncronas chamando o <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> método, que recebem um <xref:System.Action> ou <xref:System.Func%601> como um parâmetro.  O <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> método retorna um <xref:System.Windows.Threading.DispatcherOperation> ou <xref:System.Windows.Threading.DispatcherOperation%601>, que tem um <xref:System.Windows.Threading.DispatcherOperation.Task%2A> propriedade. Você pode usar o `await` palavra-chave com qualquer um de <xref:System.Windows.Threading.DispatcherOperation> ou associado <xref:System.Threading.Tasks.Task>. Se você precisar aguardar de forma síncrona a <xref:System.Threading.Tasks.Task> que é retornado por um <xref:System.Windows.Threading.DispatcherOperation> ou <xref:System.Windows.Threading.DispatcherOperation%601>, chame o <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> método de extensão.  Chamar <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> resultará em um deadlock. Para obter mais informações sobre como usar um <xref:System.Threading.Tasks.Task> para executar operações assíncronas, consulte paralelismo de tarefas.  O <xref:System.Windows.Threading.Dispatcher.Invoke%2A> método também tem sobrecargas que usam uma <xref:System.Action> ou <xref:System.Func%601> como um parâmetro.  Você pode usar o <xref:System.Windows.Threading.Dispatcher.Invoke%2A> chamadas de método para tornar síncrono, passando um delegado <xref:System.Action> ou <xref:System.Func%601>.  
  
<a name="threading_overview"></a>   
## <a name="overview-and-the-dispatcher"></a>Visão geral e o dispatcher  
 Normalmente, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos iniciam com dois threads: um para manipulação de renderização e outra para gerenciar o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. O thread de renderização é executado oculto em segundo plano enquanto efetivamente o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread recebe entrada, trata os eventos, pinta a tela e executa o código do aplicativo. A maioria dos aplicativos usa um único [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de thread, embora em algumas situações, é melhor usar várias. Abordaremos isso com um exemplo posteriormente.  
  
 O [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] itens dentro de um objeto chamado de trabalho de filas de thread um <xref:System.Windows.Threading.Dispatcher>. O <xref:System.Windows.Threading.Dispatcher> seleciona itens de trabalho em uma base de prioridade e executa cada um deles até a conclusão.  Cada [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread deve ter pelo menos um <xref:System.Windows.Threading.Dispatcher>e cada <xref:System.Windows.Threading.Dispatcher> pode executar itens de trabalho em exatamente um thread.  
  
 O truque para a criação de aplicativos dinâmicos e amigáveis é maximizar a <xref:System.Windows.Threading.Dispatcher> taxa de transferência, mantendo os itens de trabalho pequenos. Essa forma os itens nunca ficam obsoletos sentados <xref:System.Windows.Threading.Dispatcher> fila aguardando processamento. Qualquer atraso perceptível entre a entrada e a resposta pode frustrar um usuário.  
  
 Portanto, como os [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos devem para manipular operações grandes? E se o código envolver um cálculo grande ou precisar consultar um banco de dados em algum servidor remoto? Normalmente, a resposta é tratar a operação grande em um thread separado, deixando os [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread livre para atender aos itens no <xref:System.Windows.Threading.Dispatcher> fila. Quando a operação grande for concluída, ela pode relatar seu resultado para o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread para exibição.  
  
 Historicamente, [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] permite [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos sejam acessados somente pelo thread que os criou. Isso significa que um thread de segundo plano responsável por uma tarefa de execução longa não pode atualizar uma caixa de texto quando ele é concluído. [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] faz isso para garantir a integridade do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] componentes. Uma caixa de listagem poderá ter uma aparência estranha se seu conteúdo for atualizado por um thread de segundo plano durante a pintura.  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tem um mecanismo de exclusão mútua interno que garante essa coordenação. A maioria das classes no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derivam <xref:System.Windows.Threading.DispatcherObject>. Na construção, um <xref:System.Windows.Threading.DispatcherObject> armazena uma referência para o <xref:System.Windows.Threading.Dispatcher> vinculado ao thread em execução no momento. Na verdade, o <xref:System.Windows.Threading.DispatcherObject> associado ao thread que o cria. Durante a execução do programa, uma <xref:System.Windows.Threading.DispatcherObject> pode chamar seu público <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> método. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> examina o <xref:System.Windows.Threading.Dispatcher> associada ao thread atual e o compara a <xref:System.Windows.Threading.Dispatcher> referência armazenada durante a construção. Se elas não corresponderem, <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> gera uma exceção. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> se destina a ser chamado no início de cada método pertencente a um <xref:System.Windows.Threading.DispatcherObject>.  
  
 Se apenas um thread pode modificar o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], como threads em segundo plano interagem com o usuário? Um thread em segundo plano pode solicitar o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread para executar uma operação em seu nome. Isso é feito registrando um item de trabalho com o <xref:System.Windows.Threading.Dispatcher> do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread. O <xref:System.Windows.Threading.Dispatcher> classe fornece dois métodos para registrar itens de trabalho: <xref:System.Windows.Threading.Dispatcher.Invoke%2A> e <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>. Ambos os métodos agendam um delegado para execução. <xref:System.Windows.Threading.Dispatcher.Invoke%2A> é uma chamada síncrona – ou seja, ele não retorna até que o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread termina, na verdade, executar o delegado. <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> é assíncrona e retorna imediatamente.  
  
 O <xref:System.Windows.Threading.Dispatcher> ordena os elementos em sua fila por prioridade. Existem dez níveis que podem ser especificados ao adicionar um elemento para o <xref:System.Windows.Threading.Dispatcher> fila. Essas prioridades são mantidas no <xref:System.Windows.Threading.DispatcherPriority> enumeração. Informações detalhadas sobre <xref:System.Windows.Threading.DispatcherPriority> níveis podem ser encontrados no [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)] documentação.  
  
<a name="samples"></a>   
## <a name="threads-in-action-the-samples"></a>Threads em ação: Os exemplos  
  
<a name="prime_number"></a>   
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>Um aplicativo single-threaded com um cálculo de execução longa  
 A maioria dos [!INCLUDE[TLA#tla_gui#plural](../../../../includes/tlasharptla-guisharpplural-md.md)] gasta uma grande parte de seu tempo ociosa enquanto aguarda eventos que são gerados em resposta às interações do usuário. Com uma programação cuidadosa esse tempo ocioso pode ser usado de forma construtiva, sem afetar a capacidade de resposta da [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modelo de threading não permite que a entrada interrompa uma operação que ocorre no [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread. Isso significa que você deve garantir que retornará para o <xref:System.Windows.Threading.Dispatcher> periodicamente para processar eventos de entrada antes que eles se tornem obsoletos pendentes.  
  
 Considere o exemplo a seguir:  
  
 ![Captura de tela que mostra o threading de números primos.](./media/threading-model/threading-prime-numbers.png)  
  
 Este aplicativo simples faz uma contagem ascendente a partir do três, pesquisando os números primos. Quando o usuário clica o **iniciar** botão, a pesquisa começa. Quando o programa encontra um primo, ele atualiza a interface do usuário com sua descoberta. A qualquer momento, o usuário pode parar a pesquisa.  
  
 Embora seja simples o suficiente, a pesquisa de números primos poderá continuar para sempre, o que apresenta algumas dificuldades.  Se manipularmos toda a pesquisa no manipulador de eventos de clique do botão, nunca daremos a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a oportunidade de manipular outros eventos de thread. O [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] não poderá responder à entrada nem processar mensagens. Ele nunca redesenhará e nunca responderá aos cliques do botão.  
  
 Poderíamos realizar a pesquisa de números primos em um thread separado, mas precisaríamos lidar com problemas de sincronização. Com uma abordagem single-threaded, podemos atualizar diretamente o rótulo que lista o maior primo encontrado.  
  
 Se dividirmos a tarefa de cálculo em partes gerenciáveis, podemos periodicamente retornar para o <xref:System.Windows.Threading.Dispatcher> e processar eventos. Podemos dar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uma oportunidade de redesenhar e processar a entrada.  
  
 A melhor maneira de dividir o tempo de processamento entre cálculo e manipulação de eventos é gerenciar o cálculo do <xref:System.Windows.Threading.Dispatcher>. Usando o <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> método, podemos agendar verificações de números primos na mesma fila da qual [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] eventos são extraídos. Em nosso exemplo, agendamos somente uma única verificação de números primos por vez. Depois que a verificação de números primos for concluída, agendaremos a próxima verificação imediatamente. Essa verificação continua somente após pendentes [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] eventos foram tratados.  
  
 ![Captura de tela que mostra a fila do dispatcher.](./media/threading-model/threading-dispatcher-queue.png)  
  
 O [!INCLUDE[TLA#tla_word](../../../../includes/tlasharptla-word-md.md)] realiza a verificação ortográfica usando esse mecanismo. Verificação ortográfica é feita em segundo plano usando o tempo ocioso do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread. Vamos dar uma olhada no código.  
  
 O exemplo a seguir mostra o XAML que cria a interface do usuário.  
  
 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]  
  
 O exemplo a seguir mostra o code-behind.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]  
  
 O exemplo a seguir mostra o manipulador de eventos para o <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]  
  
 Além de atualizar o texto sobre o <xref:System.Windows.Controls.Button>, esse manipulador é responsável por agendar a primeira verificação de números primos adicionando um delegado para o <xref:System.Windows.Threading.Dispatcher> fila. Algum tempo depois que esse manipulador de eventos tiver concluído seu trabalho, o <xref:System.Windows.Threading.Dispatcher> selecionará esse delegado para execução.  
  
 Como mencionado anteriormente, <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> é o <xref:System.Windows.Threading.Dispatcher> membro usado para agendar um delegado para execução. Nesse caso, escolhemos o <xref:System.Windows.Threading.DispatcherPriority.SystemIdle> prioridade. O <xref:System.Windows.Threading.Dispatcher> executará esse delegado somente quando não há nenhum processamento de eventos importantes. A capacidade de resposta da [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] é mais importante do que a verificação de números. Também passamos um novo delegado que representa a rotina de verificação de números.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]  
  
 Esse método verifica se o próximo número ímpar é um primo. Se for primo, o método atualiza diretamente a `bigPrime` <xref:System.Windows.Controls.TextBlock> para refletir sua descoberta. Podemos fazer isso porque o cálculo é feito no mesmo thread que foi usado para criar o componente. Se tivéssemos escolhido usar um thread separado para o cálculo, teríamos que usar um mecanismo de sincronização mais complicado e executar a atualização no [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread. Demonstraremos essa situação a seguir.  
  
 Para o código-fonte completo para este exemplo, consulte o [aplicativo single-threaded com exemplo de cálculo de execução longa](https://go.microsoft.com/fwlink/?LinkID=160038)  
  
<a name="weather_sim"></a>   
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>Manipulando uma operação de bloqueio com um thread de segundo plano  
 A manipulação de operações de bloqueio em um aplicativo gráfico pode ser difícil. Não desejamos chamar métodos de bloqueio por meio de manipuladores de eventos, pois o aplicativo parecerá congelado. Podemos usar um thread separado para lidar com essas operações, mas quando terminamos, é necessário sincronizar com o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread porque não podemos modificar diretamente o [!INCLUDE[TLA2#tla_gui](../../../../includes/tla2sharptla-gui-md.md)] de nosso thread de trabalho. Podemos usar <xref:System.Windows.Threading.Dispatcher.Invoke%2A> ou <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> Inserir delegados na <xref:System.Windows.Threading.Dispatcher> da [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread. Eventualmente, esses representantes serão executados com permissão para modificar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos.  
  
 Neste exemplo, simulamos uma chamada de procedimento remoto que recupera uma previsão do tempo. Usamos um thread de trabalho separada para executar essa chamada e agendamos um método de atualização no <xref:System.Windows.Threading.Dispatcher> do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] quando terminamos de thread.  
  
 ![Captura de tela que mostra informações sobre o clima da interface do usuário.](./media/threading-model/threading-weather-ui.png)  
  
 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]  
  
 Veja a seguir alguns dos detalhes a serem observados.  
  
-   Criando o manipulador de botões  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]  
  
 Quando o botão recebe um clique, exibimos o desenho do relógio e iniciamos sua animação. Desabilitamos o botão. Invocamos o `FetchWeatherFromServer` método em um novo thread e, em seguida, podemos retornar, permitindo que o <xref:System.Windows.Threading.Dispatcher> processe eventos enquanto aguardamos a coleta da previsão do tempo.  
  
-   Buscando o clima  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]  
  
 Para manter as coisas simples, na verdade, não apresentamos nenhum código de rede neste exemplo. Em vez disso, simulamos o atraso do acesso à rede colocando nosso novo thread em suspensão por quatro segundos. Nesse momento, o original [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] segmento ainda está em execução e respondendo a eventos. Para mostrar isso, deixamos uma animação em execução e os botões Minimizar e Maximizar também continuam funcionando.  
  
 Quando o atraso é concluído e aleatoriamente, selecionamos nossa previsão do tempo, é hora de relatar para o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread. Fazemos isso com o agendamento de uma chamada para `UpdateUserInterface` no [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread usando esse thread <xref:System.Windows.Threading.Dispatcher>. Passamos uma cadeia de caracteres que descreve o clima para essa chamada de método agendada.  
  
-   Atualizando o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]  
  
 Quando o <xref:System.Windows.Threading.Dispatcher> no [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread tem tempo, ele executa a chamada agendada para `UpdateUserInterface`. Esse método para a animação do relógio e escolhe uma imagem para descrever o clima. Ele exibe essa imagem e restaura o botão “Buscar Previsão”.  
  
<a name="multi_browser"></a>   
### <a name="multiple-windows-multiple-threads"></a>Várias janelas, vários threads  
 Alguns [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos exigem várias janelas de nível superior. É perfeitamente aceitável para um Thread /<xref:System.Windows.Threading.Dispatcher> combinação para gerenciar várias janelas, mas às vezes, vários threads fazem um trabalho melhor. Isso será especialmente verdadeiro se houver uma possibilidade de que uma das janelas monopolize o thread.  
  
 O [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Explorer funciona desta maneira. Cada nova janela do Explorer pertence ao processo original, mas é criada sob o controle de um thread independente.  
  
 Usando um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Frame> controle, podemos exibir páginas da Web. Podemos criar facilmente um simples [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] substituir. Começamos com um recurso importante: a capacidade de abrir uma nova janela do Explorer. Quando o usuário clica no botão “Nova Janela”, iniciamos uma cópia de nossa janela em um thread separado. Dessa forma, operações de execução longa ou de bloqueio em uma das janelas não bloquearão todas as outras janelas.  
  
 Na realidade, o modelo de navegador da Web tem seu próprio modelo de threading complicado. Nós o escolhemos porque deve ser conhecido pela maioria dos leitores.  
  
 O exemplo a seguir mostra o código.  
  
 [!code-xaml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]  
  
 Os seguintes segmentos de threading desse código são os mais interessantes para nós neste contexto:  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]  
  
 Esse método é chamado quando o botão “Nova Janela” recebe um clique. Ele cria um novo thread e o inicia de forma assíncrona.  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]  
  
 Esse método é o ponto de partida para o novo thread. Criamos uma nova janela sob o controle desse thread. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] automaticamente cria um novo <xref:System.Windows.Threading.Dispatcher> para gerenciar o novo thread. Tudo o que precisamos fazer para tornar a janela funcional é iniciar o <xref:System.Windows.Threading.Dispatcher>.  
  
<a name="stumbling_points"></a>   
## <a name="technical-details-and-stumbling-points"></a>Detalhes técnicos e obstáculos  
  
### <a name="writing-components-using-threading"></a>Escrevendo componentes usando o threading  
 Guia do desenvolvedor do Microsoft .NET Framework descreve um padrão de como um componente pode expor o comportamento assíncrono para seus clientes (consulte [Event-based Asynchronous Pattern Overview](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)). Por exemplo, suponha que desejamos empacotar o `FetchWeatherFromServer` método em um componente reutilizável não gráfico. Seguindo o padrão do Microsoft .NET Framework, isso seria algo semelhante ao seguinte.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]  
  
 O `GetWeatherAsync` usaria uma das técnicas descritas anteriormente, como a criação de um thread de segundo plano, para fazer o trabalho de forma assíncrona, não bloqueando o thread de chamada.  
  
 Uma das partes mais importantes desse padrão é chamar o *MethodName* `Completed` método no mesmo thread que chamou o *MethodName* `Async` método começar. Você pode fazer isso usando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bastante fácil, armazenando <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>— mas, em seguida, o componente não gráfico só podia ser usado na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos, não no [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] programas.  
  
 O <xref:System.Windows.Threading.DispatcherSynchronizationContext> classe atende a essa necessidade – pense nela como uma versão simplificada do <xref:System.Windows.Threading.Dispatcher> que funciona com outros [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] estruturas também.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]  
  
### <a name="nested-pumping"></a>Bombeamento aninhado  
 Às vezes, não é viável completamente travar o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread. Vamos considerar o <xref:System.Windows.MessageBox.Show%2A> método da <xref:System.Windows.MessageBox> classe. <xref:System.Windows.MessageBox.Show%2A> não retorna até que o usuário clica no botão Okey. No entanto, ele cria uma janela que deve ter um loop de mensagens para ser interativa. Enquanto aguardamos até que o usuário clique em OK, a janela do aplicativo original não responde à entrada do usuário. No entanto, ele continua processando mensagens de pintura. A janela original se redesenha quando é coberta e revelada.  
  
 ![Captura de tela que mostra uma MessageBox com um botão Okey](./media/threading-model/threading-message-loop.png)  
  
 Algum thread deve ser responsável pela janela da caixa de mensagem. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poderá criar um novo thread apenas para a janela da caixa de mensagem, mas esse thread não poderá pintar os elementos desabilitados na janela original (lembre-se da discussão anterior sobre exclusão mútua). Em vez disso, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa uma sistema de processamento de mensagens aninhado. O <xref:System.Windows.Threading.Dispatcher> classe inclui um método chamado <xref:System.Windows.Threading.Dispatcher.PushFrame%2A>, que armazena o ponto de execução atual do aplicativo, em seguida, começa um novo loop de mensagem. Quando termina o loop de mensagens aninhado, a execução continua após original <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> chamar.  
  
 Nesse caso, <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> mantém o contexto do programa na chamada para <xref:System.Windows.MessageBox>.<xref:System.Windows.MessageBox.Show%2A>, e inicia um novo loop de mensagens para redesenhar a janela do plano de fundo e manipular a entrada para a janela da caixa de mensagem. Quando o usuário clica Okey e limpa a janela pop-up, o loop aninhado é encerrado e o controle continua após a chamada para <xref:System.Windows.MessageBox.Show%2A>.  
  
### <a name="stale-routed-events"></a>Eventos roteados obsoletos  
 O sistema de eventos roteados em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] notifica árvores inteiras quando os eventos são gerados.  
  
 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]  
  
 Quando o botão esquerdo do mouse é pressionado sobre a elipse, `handler2` é executado. Após `handler2` for concluída, o evento é passado para o <xref:System.Windows.Controls.Canvas> objeto, que usa `handler1` para processá-lo. Isso ocorre apenas se `handler2` faz não explicitamente marca o objeto de evento como manipulado.  
  
 É possível que `handler2` levará a uma grande quantidade de tempo de processamento esse evento. `handler2` pode usar <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> para iniciar um loop de mensagens aninhado que não retorna por horas. Se `handler2` não marca o evento como manipulado quando esse loop de mensagem for concluído, o evento é passado a árvore mesmo que ele seja muito antigo.  
  
### <a name="reentrancy-and-locking"></a>Reentrada e bloqueio  
 O mecanismo de bloqueio de [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] não se comporta exatamente como alguém poderia imaginar; podemos esperar que um thread pare a operação completamente ao solicitar um bloqueio. Na realidade, o thread continua recebendo e processando mensagens de alta prioridade. Isso ajuda a impedir bloqueios e torna a interface minimamente dinâmica, mas introduz a possibilidade de bugs sutis.  A grande maioria das vezes você não precisa saber nada sobre isso, mas em raras circunstâncias (geralmente envolvendo [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] mensagens de janela ou componentes COM STA) isso pode valer a pena saber.  
  
 A maioria das interfaces não são criadas com o acesso thread-safe em mente porque os desenvolvedores trabalham sob a suposição de que um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nunca é acessada por mais de um thread. Nesse caso, o que o único thread pode fazer alterações ambientais em momentos inesperados, causando aqueles efeitos indesejados que o <xref:System.Windows.Threading.DispatcherObject> mecanismo de exclusão mútua deverá para resolver. Considere o seguinte pseudocódigo:  
  
 ![Diagrama que mostra reentrância de threading. ](./media/threading-model/threading-reentrancy.png "ThreadingReentrancy")  
  
 Na maioria das vezes, que é a coisa certa, mas há momentos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em que essa reentrada inesperada pode realmente causar problemas. Portanto, em determinados momentos cruciais, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] chamadas <xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A>, que altera a instrução de bloqueio para esse thread usar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bloqueio livre de reentrância, em vez do habitual [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] bloqueio.  
  
 Então, por que fez a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] equipe escolheu esse comportamento? Isso tinha a ver com objetos COM STA e com o thread de finalização. Quando um objeto é coletado como lixo, seus `Finalize` método é executado no thread finalizador dedicado, não o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread. E aí está o problema, porque um objeto COM STA que foi criado a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread somente pode ser descartado no [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread. O [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] faz o equivalente a um <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (nesse caso, usando do Win32 `SendMessage`). Porém, se o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread está ocupado, o thread do finalizador será interrompido e o objeto COM STA não pode ser descartado, o que cria um vazamento de memória grave. Portanto, o [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] equipe tomou a difícil decisão para fazer com que os bloqueios funcionem da maneira que eles fazem.  
  
 A tarefa para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é evitar a reentrância inesperada sem reintroduzir a perda de memória, por isso, não bloqueamos a reentrada em todos os lugares.  
  
## <a name="see-also"></a>Consulte também

- [Amostra de aplicativo single-threaded com um cálculo de execução longa](https://go.microsoft.com/fwlink/?LinkID=160038)
