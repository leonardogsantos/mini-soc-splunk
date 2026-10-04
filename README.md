# Mini SOC — Splunk + Sysmon + Windows

Laboratório prático de Security Operations Center (SOC) construído para simular coleta de telemetria, detecção de ameaças e resposta a incidentes em um ambiente controlado.

## Arquitetura

- **Kali Linux** — Splunk Enterprise (SIEM), indexação e análise de eventos
- **Windows 11 Pro** — Endpoint monitorado, com:
  - Splunk Universal Forwarder (coleta de Windows Event Logs: Security, System, Application)
  - Sysmon (telemetria detalhada de processos, rede, arquivos) com config do [SwiftOnSecurity](https://github.com/SwiftOnSecurity/sysmon-config)
- **Splunk Add-on for Sysmon** (oficial, Splunk LLC) — normalização de campos seguindo o Common Information Model (CIM)

- 
## Cenários simulados

| Cenário | Técnica MITRE ATT&CK | Detecção |
|---|---|---|
| Força bruta de credenciais | T1110 | `EventCode=4625` com 3+ tentativas por host |
| PowerShell ofuscado (Base64) | T1059.001 / T1027 | `CommandLine="*-enc*"` em eventos Sysmon |
| Abuso de LOLBin (certutil.exe) | T1140 / T1105 | `Image="*certutil.exe"` em eventos Sysmon |

## Conteúdo do repositório

- `.pdf` — relatório completo com evidências e queries SPL
- `inputs.conf` — configuração do Universal Forwarder (Windows Event Logs + Sysmon)
- `sysmonconfig-export.xml` — configuração do Sysmon utilizada

## Autor

Leonardo Garcia Santos — [LinkedIn](https://linkedin.com/in/leonardo-garcia-santos-a81a5a1b4) | [GitHub](https://github.com/leonardogsantos)
