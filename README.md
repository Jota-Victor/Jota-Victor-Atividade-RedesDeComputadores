# Jota-Victor-Atividade-RedesDeComputadores
Atividade avaliativa feita em equipe com os seguintes membros: Joao Victor, Ronald, Lara, Giovani, Cainan e Pedro Saulo


O sistema utiliza a linguagem Python para emular o comportamento de um receptor de rede que lida com pacotes chegando fora de ordem
. A implementação foca na lógica de aceitação de pacotes dentro de uma janela permitida e no armazenamento em buffer até que a sequência correta possa ser entregue ao usuário final
.
Estruturas de Dados Utilizadas
Dicionário (self.buffer): Utilizado para armazenar pacotes recebidos fora de ordem, permitindo acesso rápido e eficiente através do número de sequência
.
Variáveis de Controle: Monitoram o tamanho da janela e o próximo número de sequência esperado (self.expected_seq)
.
Instruções Passo a Passo para Execução
1. Preparação do Código
Certifique-se de ter o Python instalado. O código base deve conter a classe SelectiveRepeatChat com os métodos de inicialização, recebimento de rede e entrega ao usuário
.
2. Configuração da Janela
Instancie a classe definindo o tamanho da janela de recepção. No cenário padrão, utilizamos o tamanho 4
: chat = SelectiveRepeatChat(window_size=4)
3. Simulação de Recebimento
Para testar o protocolo, simule a chegada de pacotes chamando o método receber_da_rede(seq_num, mensagem). Para validar a reordenação, envie os pacotes fora de ordem sequencial
.
4. Processamento e Buffering
Ao receber um pacote, o sistema realiza automaticamente as seguintes etapas:
Verificação: Checa se o número de sequência está dentro da janela válida (expected_seq <= seq_num < expected_seq + window_size)
.
Armazenamento: Se for válido e inédito, o dado é guardado no dicionário de buffer
.
Confirmação: O sistema exibe o envio de um ACK individual para o pacote recebido
.
5. Entrega ao Usuário
O método entregar_ao_usuario é disparado após cada recebimento. Ele verifica se o expected_seq está presente no buffer
. Caso esteja:
O dado é removido do buffer e exibido ao usuário
.
O contador de sequência esperada é incrementado
.
O processo se repete enquanto o próximo pacote da sequência estiver disponível
.
Cenário de Exemplo
Ao executar a simulação com a sequência de pacotes 0, 3, 1, 2, o console demonstrará que o pacote 3 foi armazenado temporariamente enquanto os pacotes 1 e 2 eram aguardados
. A entrega final ordenada resultará na frase: "Oi Giovanni tudo bem"
.
Limitações do Sistema
A versão atual da simulação apresenta as seguintes restrições:
Não simula a perda real de pacotes no meio físico
.
Não possui implementação de temporizadores (timeouts) de retransmissão
.
Não realiza verificação de corrupção de dados ou soma de verificação (checksum)
.
A comunicação é puramente lógica, sem o uso de sockets de rede reais
.
