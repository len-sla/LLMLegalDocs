# "Instructor is all you need" just --> import instructor

This repository was prepared as an kind of answer/show for one of german companies to show 
a bit how LLM could easy way (without using [CoAct framework](https://arxiv.org/pdf/2406.13381)) to make output more strict and precise
It is generating german freelance contract. Contains also piece of code to  verify and format to be used like 
LLM model is comming from OpenAI to have quick response but without any problem it could be generated locally then procedure similar 
to other of my  repository ie https://github.com/len-sla/EdgeLLM should be used


If you're working with an LLM API, integrating Pydantic is a smart choice for handling structured data efficiently. It ensures that the inputs sent to the LLM and the outputs received are validated, type-safe, and predictable, reducing the chances of errors or malformed responses. This is especially important in production AI applications where consistency matters.

Using Pydantic with LLMs also improves debugging and maintainability—you get clear error messages when things go wrong, and enforcing schemas helps keep codebases organized as your project scales. However, while it adds safety, it introduces some performance overhead and may require fallback handling for unpredictable LLM outputs.

Ultimately, if you want robust, structured, and reliable interactions with an LLM API, Pydantic is a great tool to include in your stack.

####  ![Vertrag über freie Mitarbeit ](freie_mitarbeit_vertrag-gen.ipynb)

![](llm23.gif)

# Using LLMs with Pydantic: Pros and Cons

## Pros
1. **Structured Data Validation**: Pydantic ensures that inputs and outputs of LLM interactions follow strict validation rules, improving reliability.  
2. **Automatic Type Conversion**: It converts raw LLM responses into Python objects with defined types, reducing errors in downstream processing.  
3. **Improved Debugging**: Pydantic’s detailed error messages make debugging LLM responses easier.  
4. **Integration with Async Frameworks**: Works well with FastAPI and other async-based workflows commonly used in AI applications.  
5. **Enhanced Maintainability**: Enforcing data schemas helps keep large AI-driven projects well-structured and manageable.  

## Cons
1. **Performance Overhead**: Validation and parsing can add latency, which may be noticeable in real-time applications.  
2. **Limited Handling of Unstructured Outputs**: Pydantic is great for structured data but requires extra effort to handle highly variable or unexpected LLM responses.  
3. **Version Compatibility Issues**: Pydantic v1 and v2 have different syntax and behavior, which can cause migration issues.  
4. **Potentially Overkill for Simple Use Cases**: If you only need minimal validation, Pydantic may introduce unnecessary complexity.  
5. **Strict Schema Can Cause Failures**: If the LLM output deviates from the expected schema, parsing errors might occur, requiring fallback mechanisms.  


## Good context

If an LLM isn't given good context, it tends to default to the most common or generic response because it relies on probability-based predictions. Without clear context, the model selects answers that are statistically likely based on its training data rather than those tailored to the specific situation.

that happened also in first iteration as model thought contract will be about renting an dstarted reasoning about that 
you could look at content of freie_mitarbeit_vertrag-gen.ipynb.
But after first round everything fall into place 

```
...Der Mieter ist berechtigt, die Wohnung gemäß dem vertraglich vereinbarten Zweck, nämlich zu Wohnzwecken,
 zu nutzen. Jede andere Nutzung der Wohnung bedarf der ausdrücklichen schriftlichen Zustimmung des Vermieters.
' reasoning='Diese Klausel definiert den Mietgegenstand klar und grenzt den Gebrauch auf den vertraglich vereinbarten Zweck ein,
 um potenzielle Konflikte über die Nutzung ...
```
 you could follow reasoning also with links given to BGB
like:
```
Um die vollständige Rechtssicherheit zu gewähren,
 sollten die Vertragsparteien darauf achten,
 dass keine faktischen Umstände der Ausführung die selbstständige Natur von Punkt 1 in Frage stellen.
 Weitere Details und Erläuterungen in § 611 ff. BGB verfügbar: https://www.gesetze-im-internet.de/bgb/__611a.html  ...

or

8. Salvatorische Klausel (§ 7): Diese ist rechtlich unbedenklich, gewährleistet jedoch,
 dass der Vertrag nicht komplett ungültig wird, wenn eine Klausel unwirksam ist.
\n\nUm die vollständige Rechtssicherheit zu gewähren, sollten die Vertragsparteien darauf achten,
 dass keine faktischen Umstände der Ausführung die selbstständige Natur von Punkt 1 in Frage stellen.
Weitere Details und Erläuterungen in § 611 ff. BGB verfügbar: https://www.gesetze-im-internet.de/bgb/__611a.html'
```
https://www.gesetze-im-internet.de/bgb/__611a.html


and at the end   [result](https://github.com/len-sla/LLMLegalDocs/blob/main/Firma_XYZ_GmbH_2025-02-10_11-28-29.md) was like follows:


---

# Vertrag über freie Mitarbeit

(Bitte überprüfen Sie, welche Vertragsbestimmungen übernommen werden wollen. Gegebenenfalls sind Anpassungen und Ergänzungen zu empfehlen.)

Zwischen  
Firma XYZ GmbH  
Musterstraße 1, 12345 Musterstadt  

(ggf.: vertreten durch Max Mustermann)  
- nachfolgend „Auftraggeber“ genannt -

und

Herrn/Frau John Doe  
wohnhaft Beispielweg 2, 54321 Beispielstadt  
- nachfolgend „Auftragnehmer“ genannt -

wird folgendes vereinbart:

---

## § 1 Tätigkeit

Der Auftragnehmer Softwareentwicklung wird ab dem 2025-01-01 für den Auftraggeber folgende Tätigkeiten als Auftragnehmer übernehmen: __________________. Ergänzend wird im Einzelfall auf die jeweiligen Auftragsschreiben verwiesen.

Der Auftragnehmer hat die Durchführung und den Ablauf seiner Leistung selbst zu organisieren. Er unterliegt keinen Weisungen des Auftraggebers und ist in der Gestaltung seiner Tätigkeit frei. Auf besondere betriebliche Belange im Zusammenhang mit seiner Tätigkeit ist jedoch Rücksicht zu nehmen.

Der Auftragnehmer ist an keinerlei Vorgaben zum Arbeitsort oder Arbeitszeit gebunden. Projektbezogene Zeitvorgaben des Auftraggebers sind ebenso einzuhalten wie fachliche Vorgaben, soweit diese zur ordnungsgemäßen Vertragsdurchführung erforderlich sind.

Der Auftragnehmer ist ferner berechtigt, Aufträge des Auftraggebers ohne Angaben von Gründen abzulehnen.

Gegenüber den Angestellten des Auftraggebers hat der Auftragnehmer keine Weisungsbefugnis.

---

## § 2 Leistungserbringung

Der Auftragnehmer erbringt die Arbeitsleistung in der Regel persönlich. Er kann sich zur Erfüllung des Auftrags auch anderer Personen bedienen. Die Hinzuziehung eigener Mitarbeiter oder die Vergabe von Unteraufträgen erfolgt in Abstimmung mit dem Auftraggeber. Für die ordnungsgemäße Erfüllung der vertraglichen Leistungen bleibt er dem Auftraggeber gegenüber verantwortlich.

Für die steuerlichen und sozialversicherungsrechtlichen Belange hat der freie Mitarbeiter selbst Sorge zu tragen, insbesondere auch für eine angemessene Versicherung für die Altersvorsorge wie auch zum Schutz gegen Krankheiten und den Pflegefall.

Der Auftragnehmer übt seine Tätigkeit in seinen eigenen Räumlichkeiten aus. Soweit in Einzelfällen eine betriebliche Anwesenheit erforderlich wird, stellt der Auftraggeber nach jeweiliger vorheriger Absprache die entsprechenden betrieblichen Einrichtungen zur Verfügung. Der Auftraggeber stellt dem Auftragnehmer alle zur Ausübung seiner Tätigkeiten erforderlichen Informationen, Hilfsmittel und Unterlagen zur Verfügung.

---

## § 3 Vergütung

Als Vergütung wird ein Stundenhonorar von 80.0 € zuzüglich der jeweiligen gesetzlichen Mehrwertsteuer vereinbart. Der Auftragnehmer ist verpflichtet, jeweils bis zum Zehnten des Folgemonats eine spezifizierte Abrechnung in Form einer Rechnung zu erstellen.

Das vereinbarte pauschale Honorar wird jeweils am Monatsende fällig. Die Auszahlung erfolgt unbar.

Der Auftragnehmer wird innerhalb von 14 Tagen nach Beginn der Zusammenarbeit dem Auftraggeber ein Konto benennen, auf das das Honorar angewiesen werden kann.

---

## § 4 Aufwendungsersatz und sonstige Ansprüche

Mit der Zahlung der in diesem Vertrag vereinbarten Vergütung sind alle Ansprüche des Auftragnehmers gegen den Auftraggeber aus diesem Vertrag erfüllt.

oder

Der Auftragnehmer hat Anspruch auf Ersatz der abgerechneten und nachgewiesenen Aufwendungen, die ihm im Rahmen dieser Vereinbarung in der Ausübung seiner Tätigkeit entstehen. Das Normalmaß erheblich übersteigende Ausgaben werden jedoch nur dann ersetzt, wenn der Auftragnehmer zuvor die Zustimmung des Auftraggebers eingeholt hat. Für die Versteuerung der Vergütung hat der Auftragnehmer selbst zu sorgen.

Der Auftragnehmer wird darauf hingewiesen, dass er nach § 2 Nr. 9 SGB VI rentenversicherungspflichtig sein kann, wenn er auf Dauer und im Wesentlichen nur für einen Auftraggeber tätig ist.

---

## § 5 Haftung und Gewährleistung

Sollte der Auftraggeber auf Grund von Leistungen, die vom Auftragnehmer erbracht wurden, in Haftung genommen werden, so verpflichtet sich der Auftragnehmer gegenüber dem Auftraggeber, diesen von derlei Haftung freizustellen.

Für Schäden, die durch Zeitüberschreitung des Auftragnehmers erfolgen, ist die Haftung des Auftragnehmers auf die Höhe von 5000.0 € begrenzt. Im Übrigen verpflichtet sich der Auftragnehmer zur kostenlosen Nacharbeit und Beseitigung der von ihm verursachten Mängel.

---

## § 6 Fortbildungspflicht

Der Auftragnehmer ist verpflichtet, sich im Rahmen der Durchführung dieses Vertrages auf dem Gebiet seiner Tätigkeit über den aktuellen Entwicklungsstand weiterzubilden und sich über aktuelle Veränderungen auf diesem Gebiet jederzeit auf dem Laufenden zu halten.

---

## § 7 Konkurrenz

Der Auftragnehmer darf auch für andere Auftraggeber tätig sein. Will der Auftragnehmer allerdings für einen unmittelbaren Wettbewerber des Auftraggebers tätig werden, bedarf dies der vorherigen schriftlichen Zustimmung des Auftraggebers.

Der Auftragnehmer verpflichtet sich, für jeden Fall der Zuwiderhandlung eine Vertragsstrafe in Höhe von 10000.0 € zu zahlen.

---

## § 8 Verschwiegenheit, Aufbewahrung und Rückgabe von Unterlagen

Die Vertragsparteien verpflichten sich, alle ihnen im Rahmen des Vertrages zugänglich gemachten, sowie bei Gelegenheit der Zusammenarbeit erlangten Informationen über Angelegenheiten der anderen Partei, die als vertraulich gekennzeichnet sind; die bei einer mündlichen Übermittlung als vertraulich bezeichnet werden; oder die aus Sicht eines objektiven Beobachters als vertraulich erkennbar sind; sowie Geschäfts- und Betriebsgeheimnisse vertraulich zu behandeln. Vertrauliche Informationen dürfen ohne schriftliche Einwilligung der anderen Vertragspartei zu einem anderen als dem zur vertragsgemäßen Aufgabenerfüllung vorgesehenen Zweck nicht verwertet, Dritten zugänglich gemacht oder sonst genutzt werden.

Die Parteien tragen dafür Sorge, dass Dritte, derer sie sich als Erfüllungsgehilfen bedienen, ebenfalls die Geheimhaltungspflicht beachten.

Für jeden Fall der schuldhaften Verletzung dieser Verpflichtungen wird eine Vertragsstrafe in Höhe von 20000.0 € vereinbart.

Weitergehender Schadensersatz sowie die Geltendmachung von Unterlassungsansprüchen bleiben vorbehalten.

---

## § 9 Vertragsdauer und Kündigung

Der Auftragnehmer nimmt die Tätigkeit am 2025-01-01 auf.

Das Vertragsverhältnis kann unter Einhaltung einer Frist von 4 Wochen/Monaten zum 2025-12-31 gekündigt werden. Das Recht zur außerordentlichen Kündigung bleibt hiervon unberührt. Jede Kündigung bedarf zu ihrer Wirksamkeit der Schriftform.

---

## § 10 Erfüllungsort und Gerichtsstand

Erfüllungsort und Gerichtsstand ist ____________.

---

## § 12 Nebenabreden und salvatorische Klausel

Nebenabreden und Änderungen des Vertrages bedürfen zu ihrer Wirksamkeit der Schriftform. Dieses Formerfordernis kann weder mündlich noch stillschweigend aufgehoben oder außer Kraft gesetzt werden.

Die teilweise oder vollständige Unwirksamkeit einzelner Bestimmungen dieses Vertrages berührt nicht die Wirksamkeit der übrigen Regelungen des Vertrages.

---

## § 13 Vertragsaushändigung

Jede der Vertragsparteien hat eine schriftliche Ausfertigung dieses Vertrages erhalten.

---

Ort, Datum: 

Unterschrift Auftraggeber: ___________________  
Unterschrift Auftragnehmer: ___________________

    



### If you want more info
lencz.sla@gmail.com


## Useful Resources  
- **Pydantic Docs**: [https://docs.pydantic.dev](https://docs.pydantic.dev)  
- **Example of Using Pydantic with LLMs**: [GitHub Repo](https://github.com/pydantic/pydantic/issues/5796)  
- **FastAPI + Pydantic for AI Applications**: [FastAPI Docs](https://fastapi.tiangolo.com/tutorial/body/)  
- **Handling LLM Outputs with Pydantic**: [Blog Post](https://sebastianraschka.com/blog/2023/llm-data-validation.html)  
