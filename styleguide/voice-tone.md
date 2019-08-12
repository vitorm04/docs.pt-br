---
ms.openlocfilehash: cb8cc6574caad6da25b3fced70c58175a33ec896
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68616326"
---
# <a name="voice-and-tone-guidelines"></a>Diretrizes de voz e tom

Uma ampla variedade de pessoas, incluindo profissionais de TI e desenvolvedores, lê os documentos de sua autoria para aprender a usar o .NET e usá-lo no trabalho normal.
Sua meta é criar uma documentação excelente que ajude o leitor em sua jornada. Nossas diretrizes ajudam com isso. Nosso guia de estilo contém as seguintes recomendações:
- [Usar um tom de conversa](#use-a-conversational-tone)
- [Escrever na Segunda Pessoa](#write-in-2nd-person)
- [Usar voz ativa](#use-active-voice)
- [Direcionar a um nível de leitura da 5ª série](#target-a-fifth-grade-reading-level)
- [Evitar o uso de verbos no futuro](#avoid-future-tense)
- [O que é isso? – e daí?](#what-is-it-so-what)

Você poderá ver exemplos de cada uma delas durante a leitura deste guia de estilo. Elaboramos este guia seguindo nossas diretrizes, a fim de fornecer exemplos para você seguir ao criar uma documentação para o .NET. Também fornecemos exemplos contrastantes para que você veja a aparência de artigos quando você não segue as diretrizes.

## <a name="details-on-each-guideline"></a>Detalhes de cada diretriz

### <a name="use-a-conversational-tone"></a>Usar um tom de conversa
#### <a name="appropriate-style"></a>Estilo apropriado:
Queremos que nossa documentação tenha um tom de conversa. Você deve se sentir como se você estiver tendo uma conversa com o autor ao ler qualquer um dos nossos tutoriais ou explicações.
Para você, a experiência deve ser informal, interativa e informativa. Os leitores devem se sentir como se estivessem ouvindo o autor explicando os conceitos para eles.

#### <a name="inappropriate-style"></a>Estilo inapropriado:
Quando nota-se o contraste entre um estilo de conversa e um estilo que pode ser considerado com tratamentos mais acadêmicos de tópicos técnicos. Esses recursos são muito úteis, mas os autores tem escrito esses artigos em um estilo muito diferente do nossa documentação. Quando alguém lê um diário acadêmico, nota o estilo muito diferente, além do estilo de escrita.
Parece que alguém está lendo uma conta rígida sobre um tópico rígido.  

O primeiro parágrafo acima segue nosso estilo conversacional de recomendação. O segundo é um estilo mais acadêmico. Você poderá ver a diferença imediatamente. 

### <a name="write-in-second-person"></a>Escrever na segunda pessoa
#### <a name="appropriate-style"></a>Estilo apropriado:
Você deve escrever artigos como se estivesse falando diretamente para o leitor. Você deve usar a segunda pessoa com frequência (como fiz nessas duas frases). A 2ª pessoa nem sempre significa o uso da palavra 'você’. Escreva diretamente para o leitor. Escreva frases imperativas.
Informe o leitor o que você deseja ensinar.

#### <a name="inappropriate-style"></a>Estilo inapropriado: 
Um autor também pode optar por escrever na terceira pessoa. Nesse modelo, um autor deve encontrar alguns pronomes ou substantivos para usar ao se referir ao leitor. Um leitor pode, muitas vezes, achar que esse estilo de terceira pessoa seja menos envolvendo e menos agradável para leitura.

O primeiro parágrafo segue nosso estilo recomendado. O segundo usa a terceira pessoa. Escreva na segunda pessoa. Provavelmente, você achará muito mais fácil de ler.

### <a name="use-active-voice"></a>Usar voz ativa

Escreva seus artigos em voz ativa. Voz ativa significa que o assunto da sentença executa a ação (verbo) daquela frase. Ela contrasta com a voz passiva, em que a frase é organizada de modo com a ação baseia-se no assunto da sentença. Compare esses dois exemplos:

>O compilador transformou o código-fonte em um executável.

>O código-fonte foi transformado em um executável pelo compilador.

A primeira sentença usa voz ativa. A segunda frase foi escrita em voz passiva.
(Essas duas frases fornecem outro exemplo de cada estilo).

É recomendável voz ativa por ser mais legível. A voz passiva pode ser mais difícil de ler.

### <a name="target-a-fifth-grade-reading-level"></a>Direcionar um nível de leitura de 5ª série

Fornecemos essa diretriz final porque muitos de nossos leitores não são falantes de inglês nativos.
Você alcançará um público internacional com seus artigos. Leve em conta que eles podem não ter o vocabulário em inglês que você tem.

No entanto, você ainda escreverá pra profissionais técnicos. Você pode supor que os leitores tenham conhecimento de programação e vocabulário específico para termos de programação. Programação orientada a objeto, classe e objeto, função e método são termos conhecidos. No entanto, nem todos os leitores de seus artigos tem uma graduação formal em ciência da computação. Termos como "idempotente" provavelmente precisarão ser definidos se você usá-los:

>O método Close() é idempotente, que significa que você pode chamá-lo várias vezes e o efeito é o mesmo como se você chamado uma vez.

### <a name="avoid-future-tense"></a>Evitar o uso de verbos no futuro
Em alguns idiomas, exceto o inglês, o conceito de uso de verbos no futuro não é o mesmo que no inglês. O uso de verbos no futuro pode dificultar a leitura dos documentos de sua autoria. Além disso, ao usar verbos no futuro, a pergunta óbvia é quando usá-los. Portanto, se você disser "Será útil aprender a usar o PowerShell", a questão óbvia para o leitor será "Quando isso será útil?". Em vez disso, basta dizer "É útil aprender a usar o PowerShell".

### <a name="what-is-it---so-what"></a>O que é isso? – e daí?
Sempre que você introduzir um novo conceito ao leitor, defina o conceito e, em seguida, explique por que ele é útil. É importante que o leitor entenda o que é algo para entender os benefícios (ou de outro modo). 
