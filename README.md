# S2TypescriptTypes

```typescript
export interface S2AuthorAsSecondarySmall {
  authorId: string;
  name?: string;
}

export type S2AuthorExternalIds = {
  ORCID?: string;
  DBLP?: string[];
};

export interface S2AuthorAsSecondaryLarge extends S2AuthorAsSecondarySmall {
  externalIds: S2AuthorExternalIds;
  url?: string;
  aliases?: string[];
  affiliations?: string[];
  homepage?: string;
  paperCount?: number;
  citationCount?: number;
  hIndex?: number;
}

export interface S2Author extends S2AuthorAsSecondaryLarge {
  papers?: S2ResearchPaperAsSecondary[];
}

export enum S2ResearchPaperPublicationType {
  review = 'Review',
  journalArticle = 'JournalArticle',
  news = 'News',
  study = 'Study',
  lettersAndComments = 'LettersAndComments',
  editorial = 'Editorial',
  clinicalTrial = 'ClinicalTrial',
}

export enum S2FieldOfStudy {
  agriculturalAndFoodSciences = 'Agricultural and Food Sciences',
  art = 'Art',
  biology = 'Biology',
  business = 'Business',
  computerScience = 'Computer Science',
  chemistry = 'Chemistry',
  economics = 'Economics',
  education = 'Education',
  engineering = 'Engineering',
  environmentalScience = 'Environmental Science',
  geography = 'Geography',
  geology = 'Geology',
  history = 'History',
  law = 'Law',
  linguistics = 'Linguistics',
  materialsScience = 'Materials Science',
  mathematics = 'Mathematics',
  medicine = 'Medicine',
  philosophy = 'Philosophy',
  physics = 'Physics',
  politicalScience = 'Political Science',
  psychology = 'Psychology',
  sociology = 'Sociology',
}

export type S2ResearchPaperExternalIds = {
  MAG: string;
  ArXiv: string;
  ACL: string;
  PubMed: string;
  Medline: string;
  PubMedCentral: string;
  DBLP: string;
  DOI: string;
  CorpusId: number;
};

export interface S2ResearchPaperAsSecondary {
  paperId: string;
  externalIds: S2ResearchPaperExternalIds;
  url?: string;
  title?: string;
  abstract?: string;
  venue?: string;
  year?: number;
  referenceCount?: number;
  citationCount?: number;
  influentialCitationCount?: number;
  isOpenAccess?: boolean;
  fieldsOfStudy?: S2FieldOfStudy[];
  s2FieldsOfStudy?: {
    category: S2FieldOfStudy | string;
    source: 'external' | 's2-fos-model' | string;
  }[];
  publicationTypes?: S2ResearchPaperPublicationType[];
  // In the YYYY-MM-DD format
  publicationDate?: string;
  journal?: {
    name: string;
    volume: string;
    pages: string;
  };
  authors?: S2AuthorAsSecondarySmall[];
}

export interface S2ResearchPaper extends S2ResearchPaperAsSecondary {
  references?: S2ResearchPaperAsSecondary[];
  citations?: S2ResearchPaperAsSecondary[];
  tldr?: {
    models: string;
    text: string;
  };
  embedding?: {
    model?: string;
    vector?: number[];
  };
  authors?: S2AuthorAsSecondaryLarge[];
}
```
