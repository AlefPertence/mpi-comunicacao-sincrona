# MPI — Comunicação Síncrona

Projeto desenvolvido em Python utilizando MPI (Message Passing Interface) e as bibliotecas `mpi4py` e `NumPy`, com o objetivo de demonstrar a comunicação síncrona entre processos.

## Objetivo

Demonstrar o funcionamento do envio síncrono de mensagens utilizando `Ssend()`, observando como um processo pode aguardar até que o processo destinatário inicie a recepção correspondente.

## Funcionamento

- O rank 0 prepara um número inteiro para envio.
- O rank 1 aguarda um intervalo de tempo configurável antes de iniciar a recepção.
- O rank 0 utiliza `Ssend()` para enviar a mensagem ao rank 1.
- O rank 1 recebe a mensagem por meio de `Recv()`.
- Após receber o valor, o rank 1 realiza uma operação matemática: `2 × valor + 1`.
- O rank 1 envia o resultado de volta ao rank 0 utilizando `Ssend()`.
- O rank 0 recebe a resposta, realiza a conferência e apresenta o tempo de duração do primeiro envio síncrono.

## Tecnologias utilizadas

- Python
- MPI (Message Passing Interface)
- mpi4py
- NumPy

## Execução

O programa deve ser executado com exatamente dois processos MPI.

```bash
mpiexec -n 2 python pratica4_mensagens_sincronas.py --valor 21 --atraso 1.0
```

### Parâmetros

| Parâmetro | Descrição |
|---|---|
| `-n 2` | Define a execução com dois processos MPI. |
| `--valor 21` | Define o número que será enviado pelo rank 0. |
| `--atraso 1.0` | Define o tempo de espera do rank 1 antes de receber a mensagem, em segundos. |

## Conceitos abordados

- Comunicação entre processos
- Envio síncrono
- Envio e recebimento de mensagens
- Processos MPI e ranks
- Sincronização
- `MPI.COMM_WORLD`
- `Barrier()`
- `Ssend()`
- `Recv()`
- `MPI.Wtime()`

## Observação

O envio síncrono `Ssend()` é uma operação bloqueante que depende do início da recepção correspondente. O atraso configurado no rank 1 permite observar o comportamento do rank 0 durante a tentativa de envio.

O exercício exige exatamente dois processos MPI e possui finalidade didática.

---

Projeto acadêmico desenvolvido para fins de estudo de comunicação entre processos e programação paralela.
