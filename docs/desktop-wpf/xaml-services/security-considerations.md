---
title: Considerações sobre segurança XAML
ms.date: 03/30/2017
helpviewer_keywords:
- security [XAML Services], .NET XAML services
- XAML security [XAML Services]
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
ms.openlocfilehash: 1864910b339c74e3033fb4d6d8baebffada1a4f8
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071685"
---
# <a name="xaml-security-considerations"></a>Considerações de segurança XAML

Este artigo descreve as melhores práticas de segurança em aplicativos quando você usa a API de Serviços XAML e .NET XAML.

## <a name="untrusted-xaml-in-applications"></a>XAML não confiável em aplicativos

No sentido mais geral, xaml não confiável é qualquer fonte XAML que seu aplicativo não incluiu ou emitia especificamente.

O XAML que é compilado `resx`ou armazenado como um recurso de tipo dentro de uma montagem confiável e assinada não é inerentemente inconfiável. Você pode confiar no XAML tanto quanto confia na assembléia como um todo. Na maioria dos casos, você só está preocupado com os aspectos de confiança do XAML solto, que é uma fonte XAML que você carrega de um fluxo ou de outros I/O. Loose XAML não é um componente específico ou característica de um modelo de aplicativo com uma infra-estrutura de implantação e embalagem. No entanto, um conjunto pode implementar um comportamento que envolve carregar XAML solto.

Para XAML não confiável, você deve tratá-lo geralmente como se fosse um código não confiável. Use sandboxing ou outras metáforas para evitar que xaml possivelmente não confiável acesse seu código confiável.

A natureza dos recursos XAML dá ao XAML o direito de construir objetos e definir suas propriedades. Esses recursos também incluem acessar conversores de tipo, mapear e acessar conjuntos `x:Code` no domínio do aplicativo, usando extensões de marcação, blocos e assim por diante.

Além de seus recursos em nível de idioma, o XAML é usado para definição de interface do ui em muitas tecnologias. Carregar XAML não confiável pode significar carregar uma ui de falsificação maliciosa.

## <a name="sharing-context-between-readers-and-writers"></a>Compartilhar contexto entre leitores e escritores

A arquitetura .NET XAML Services para leitores XAML e escritores XAML muitas vezes requer compartilhar um leitor XAML com um escritor XAML ou um contexto de esquema XAML compartilhado. Compartilhar objetos ou contextos pode ser necessário se você estiver escrevendo a lógica de loop do nó XAML ou fornecendo um caminho de salvamento personalizado. Não compartilhe instâncias de leitor XAML, contexto de esquema XAML não padrão ou configurações para classes de leitor/escritor XAML entre código confiável e não confiável.

A maioria dos cenários e operações envolvendo a gravação de objetos XAML para um backup de tipo baseado em CLR pode apenas usar o contexto padrão do esquema XAML. O contexto padrão do esquema XAML não inclui explicitamente configurações que possam comprometer a confiança total. Portanto, é seguro compartilhar o contexto entre componentes confiáveis e não confiáveis do leitor/escritor XAML. No entanto, se você fizer isso, ainda é uma <xref:System.AppDomain> prática recomendada manter tais leitores e escritores em escopos separados, com um deles especificamente destinado/sandboxed para confiança parcial.

## <a name="xaml-namespaces-and-assembly-trust"></a>XAML Namespaces e Assembly Trust

A sintaxe e definição básicas não qualificadas para como o XAML interpreta um mapeamento de namespace XAML personalizado para um conjunto não distingue entre um conjunto confiável e não confiável como carregado no domínio do aplicativo. Assim, é tecnicamente possível que uma montagem não confiável anule o mapeamento de namespace XAML pretendido por um conjunto confiável e capture as informações de objeto e propriedade declaradas de uma fonte XAML. Se você tiver requisitos de segurança para evitar essa situação, o mapeamento de namespace XAML pretendido deve ser feito usando uma das seguintes técnicas:

- Use um nome de montagem totalmente qualificado com nome forte em qualquer mapeamento de namespace XAML feito pelo XAML do seu aplicativo.

- Restringir o mapeamento de montagem a um conjunto fixo <xref:System.Xaml.XamlSchemaContext> de conjuntos de referência, construindo um específico para seus leitores XAML e escritores de objetos XAML. Consulte <xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>.

## <a name="xaml-type-mapping-and-type-system-access"></a>Mapeamento do tipo XAML e acesso ao sistema de tipo

XAML suporta seu próprio sistema de tipo, que em muitos aspectos é um peer de como a CLR implementa o sistema básico do tipo CLR. No entanto, para certos aspectos da consciência do tipo onde você está tomando decisões de confiança sobre um tipo com base em suas informações de tipo, você deve adiar para as informações de tipo nos tipos de apoio CLR. Isso ocorre porque alguns dos recursos específicos de emissão de relatórios do sistema do tipo XAML são deixados abertos como métodos virtuais e, portanto, não estão totalmente sob o controle das implementações originais do .NET XAML Services. Esses pontos de extensibilidade existem porque o sistema do tipo XAML é extensível, para corresponder à extensibilidade do próprio XAML e suas possíveis estratégias alternativas de mapeamento de tipos em comparação com a implementação padrão apoiada pela CLR e o contexto padrão do esquema XAML. Para obter mais informações, consulte as notas <xref:System.Xaml.XamlType> <xref:System.Xaml.XamlMember>específicas sobre várias das propriedades de e .

## <a name="see-also"></a>Confira também

- <xref:System.Xaml.Permissions.XamlAccessLevel>
