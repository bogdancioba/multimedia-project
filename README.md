1. Obiectivul proiectului:
Scopul principal este de a antrena un model SVM pentru a clasifica imagini bazându-se pe diverse caracteristici extrase din acele imagini.
2. Fluxul de lucru (workflow):

Încărcarea imaginilor din directoarele "genuine" și "spoofed".
Extragerea unui set de caracteristici de la fiecare imagine, inclusiv:
Coerența spațială
Factorul de clusterizare
Caracteristicile Gabor
Uniformitatea câmpului de frecvență
Frecvența crestei
Harta direcției
Harta contrastului redus
Separarea datelor în seturi de antrenare și testare.
Antrenarea unui clasificator SVM pe setul de antrenare.
Evaluarea performanței clasificatorului pe setul de testare și afișarea rezultatelor.
3. Detalii și explicații pentru fiecare funcție:

a) get_image_files_from_directory(directory):
Această funcție returnează toate fișierele de imagine dintr-un director specificat.

b) spatial_coherence(image):
Măsoară coerența spațială a imaginii prin calculul gradientului și folosind magnitudinea acestuia ca măsură.

c) clustering_factor(image):
Calculează factorul de clusterizare bazat pe numărul de pixeli negri în vecinătatea 3x3.

d) gabor_feature(image):
Extrage caracteristicile Gabor, cum ar fi media și deviația standard a răspunsului filtrului Gabor.

e) uniformity_of_frequency_field(image) și altele:
Aceste funcții calculează diferite caracteristici ale imaginii, cum ar fi uniformitatea câmpului de frecvență, frecvența crestei, harta direcției și harta contrastului redus.

f) extract_features_from_image(image_path):
Aceasta este o funcție agregată care extrage toate caracteristicile de mai sus pentru o imagine dată.

4. Antrenare și evaluare:
După extragerea caracteristicilor, modelează datele pentru antrenarea unui SVM. Antrenează SVM pe setul de antrenare și evaluează pe setul de testare.
Performanța este apoi evaluată folosind precizia, reamintirea, f1-score și matricea de confuzie.

5. Vizualizări:
Pentru o analiză mai profundă, afișez matricea de confuzie și imaginile clasificate incorect pentru a înțelege unde modelul s-ar putea îmbunătăți.

Rezultate:
Din rezultatele obținute, se pare că modelul are o acuratețe de aproximativ 67% pe setul de testare. Având în vedere rezultatele matricii de confuzie și raportul de clasificare,
 putem spune că modelul are un echilibru între detectarea imaginilor autentice și a celor falsificate.

În concluzie, proiectul demonstrează cum putem folosi tehnici de procesare a imaginilor și machine learning pentru a clasifica imagini în funcție de caracteristicile lor.
 Cu toate acestea, acuratețea ar putea fi îmbunătățită cu mai multe date sau folosind un model mai complex.
 
 


Spatial Coherence: Măsoară coerența spațială a unei imagini. Acest lucru este realizat prin calculul gradientului imaginii și apoi calculul mediei magnitudinii acestui gradient.
 Imaginile originale și cele falsificate pot avea diferite nivele de coerență spațială.

Clustering Factor: Calculează factorul de grupare al unei imagini prin binarizarea acesteia și apoi prin numărarea pixelilor negri într-o vecinătate de 3x3.

Gabor Feature: Se folosește un filtru Gabor pentru a extrage anumite caracteristici din imagine. În acest context, se extrag media și deviația standard a imaginii filtrate cu filtrul Gabor.

Uniformity of Frequency Field: Măsoară uniformitatea domeniului de frecvență al imaginii, calculând varianța unui histogram al orientărilor gradientului.

Ridge Frequency: Estimează frecvența crestei unei imagini bazată pe orientarea gradientului.

Direction Map: Reprezintă harta direcției imaginii bazată pe orientarea gradientului.

Low Contrast Map: Calculează harta contrastului redus a imaginii în blocuri de o dimensiune specificată.

Programul combină aceste caracteristici pentru fiecare imagine și le utilizează pentru a antrena un clasificator SVM (Support Vector Machine).
 Clasificatorul învață modelul care separă cel mai bine imaginile originale de cele falsificate pe baza caracteristicilor furnizate.

Odată ce modelul este antrenat, el poate fi folosit pentru a prezice dacă o imagine necunoscută este originală sau falsificată pe baza caracteristicilor ei.
Evaluarea realizată (matricea de confuzie, raportul de clasificare etc.) oferă informații despre cât de bine funcționează clasificatorul pe setul de date de test.

Este important de menționat că eficacitatea acestui sistem depinde de calitatea și varietatea datelor de antrenament, precum și de relevanța caracteristicilor selectate pentru problema în cauză.
 Dacă caracteristicile nu sunt relevante sau dacă setul de date nu este reprezentativ, performanța sistemului ar putea fi suboptimală.
 
 
Gabor :  
 
ksize: Reprezintă dimensiunea nucleului Gabor. În acest caz, nucleul are dimensiunea de 31x31.

sigma: Este deviația standard a funcției Gaussiene din filtrul Gabor. Determină lățimea benzii de frecvențe pe care filtrul o va capta.

theta: Este orientarea nucleului Gabor. În acest caz, este setată la 45 de grade sau π/4 radieni.

lambd: Este lungimea de undă a componentei sinusoidale a filtrului Gabor.

gamma: Este raportul de aspect și determină elipticitatea nucleului.

psi: Este faza offset a funcției sinusoidale.
