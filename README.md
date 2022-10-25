# S2TypescriptTypes

```typescript
export interface S2AuthorAsSecondarySmall {
  authorId: string;
  name?: string;
}

export interface S2AuthorAsSecondaryLarge extends S2AuthorAsSecondarySmall {
  externalIds: {
    ORCID?: string;
    DBLP?: string[];
  };
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
  Review = 'Review',
  JournalArticle = 'JournalArticle',
  News = 'News',
  Study = 'Study',
  LettersAndComments = 'LettersAndComments',
  Editorial = 'Editorial',
  ClinicalTrial = 'ClinicalTrial',
}

export interface S2ResearchPaperAsSecondary {
  paperId: string;
  externalIds?: {
    MAG?: string;
    ArXiv?: string;
    ACL?: string;
    PubMed?: string;
    Medline?: string;
    PubMedCentral?: string;
    DBLP?: string;
    DOI?: string;
    CorpusId?: number;
  };
  title?: string;
  abstract?: string;
  venue?: string;
  year?: number;
  referenceCount?: number;
  citationCount?: number;
  influentialCitationCount?: number;
  isOpenAccess?: boolean;
  fieldsOfStudy?: string[];
  s2FieldsOfStudy?: {
    category: string;
    source: 'external' | 's2-fos-model' | string;
  };
  publicationTypes?: S2ResearchPaperPublicationType[];
  // In the YYYY-MM-DD format
  publicationDate?: string[];
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
}
```
